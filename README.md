# OPT-Same-Key-Used

參考：https://www.twblogs.net/a/5b7f42bf2b717767c6aea640 

作法:
I. 先將 10 個 ciphertexts 分別兩個兩個做一次 XOR 共 90 次，發現在某幾個位置使用某一個 ciphertext A 和其他 9 個 ciphertexts 做 XOR 時，都會解出字元或數字出來，那代表 ciphertext A    的這個位置解出來的明文可能是空白， 只要找到每個位置相對應的 ciphertext A 可能在明文出現空白就可以將此 ciphertext A 的該位置的密文和空白做 XOR 即可得到 Key 在該位置可能的 值。


II. 但因為可會某些位置會有很多個可能 ciphertext A，首先採用第一個找到的 候選人來解出全部的 key，再將 key 和 target ciphertext 做 XOR 解出 target 的明文，再透過 doMicroAdjust 方       法，將明文中的錯字猜測成可能符合前後 文的字母，並將該字母和該位置的 target ciphertext 做 XOR 來更新 key 在該 位置的值，如此一來逐一更新即可得到完整的 key 和 target message。
