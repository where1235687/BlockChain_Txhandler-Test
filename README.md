# BlockChain_Txhandler-Test

1. Overview
This homework mainly consists of two parts. The first one is to complete the class, “TxHandler”, which is used to check whether a transaction is valid and handle it (eg., handle UTRANSACTIONO and UTRANSACTIONO pool, generate a valid transaction list, etc.). The other is to generate seven test suites to test the methods in “TxHandler”. 

2. Summarize – TransactionHandler.java
In this class, there has three methods. And I will introduce those in this report briefly. The code could be found in /src/TransactionHandler.java

2.1 Constructor
“UTRANSACTIONOPool” is the only attribute of the “TransactionHandler” class. So constructor do the make a defensive copy by setting the utransactionoPool a private object, and import a new copy.
 

2.2 isValidTx(Transaction transaction)
Check whether the Transaction meets the specified requirements. If any of the requirements is not met, return false.(the details of the code can be find in the TransactionHandler.java file)The implementation is as follows:
For the first three conditions we can use a for loop to test each transaction. Create a number of UTRANSACTIONO from the prevTxHash and output index.
(1) Check if any output claimed by transaction is in the current UTRANSACTIONO pool
(2) Check no UTRANSACTIONO is claimed multiple times by transaction
(3) Use crypto. verifySigniture() provided to test the signature on each input of transaction are valid or not
(4) Check if any of transaction's output values are no-negative
(5) Check if the sum of transaction's input values is more than the sum of its output values

2.3 handleTx(Transaction[] possibleTx)
For each Transaction transaction in the possible Transactions. If we accepted this transaction, remove spent UTRANSACTIONOs from UTRANSACTIONOPool and then add new UTRANSACTIONOs to UTRANSACTIONOPool through two for loop. In this method we use the removeUTRANSACTIONO and addUTRANSACTIONO to achieve. Finally, it will return the acceptedTransactionArray array.
 

3. Test
There has 9 test used in this part. And before the test, I generate the information needed in the test.
(1) is used to test if all the outputs are in UTXOPool.
  
(2) is used to test if the private key is valid.
One input and one output
  
(3) is used to test if there has more than one output.
  
(4) is used to test if the sum of the output is not large than the input.
Receiver receives more than Sender sends

(5) is used to test if the private key belongs to the right user.
Sender send coins to receiver, but the sign is belonging to receiver.
  
(6) is used to test if it is the double spending.
One transaction uses twice.

(7) is used to test if the outputs is not negative.
Set the output value is Negative.

(8) is used to test if the claims are only one time.
Same Input and Sign are used more than once.
 
(9) is used to test if the Pool is updated.

4. Conclusion
All of the methods used in "TransactionHandler.java" are confirmed using the nine test suites in the previous section.
 
