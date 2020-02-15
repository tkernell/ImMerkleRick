# ImMerkleRick


1. We have a document segmented into clauses.  For this example, lets say our document contains 2 clauses.

  Doc = [c1, c2]

2. Encrypt the document using a one time pad stream of data and segment the pad data in regards to the clauses it encrypts.

  OTP = [K1, K2]   -> where K1 encrypts c1, K2 encrypts c2

3. Create a merkle root from our document clauses.

     Root -> R(doc)
     /  \ 
  H(c1) H(c2)
   |     |
   c1    c2
   
   
4. Create a merkle root from our OTP key stream segments.  This will later prove the OTP key was not changed and can provide partial data validation without revealing the whole key/document if need be.

     Root -> R(otp)
     /  \ 
  H(K1) H(K2)
   |     |
   K1    K2
   
   
5. Encrypt the document with the OTP key stream:
  
  Encrypted_Doc = [K1^c1, K2^c2]
  
  
6. Store Merkle Roots of both the document and the OTP key data in smart contract.


Thoughts:
- What about storing merkle root of OTP key & the merkle root of encrypted document?  If multiple parties use the same document language (clauses), we dont want to leak data about similarities of document content by storing the same merkle roots associated to the documents.



