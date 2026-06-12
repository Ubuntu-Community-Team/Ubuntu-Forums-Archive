---
title: "WPA-PSK crack using dictionary"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by lepel on 2010-05-01
I'm trying to understand the entire method of cracking a wireless network using aircrack.
I thought the idea is to collect a lot of encrypted packets, and then try to crack these using the fact that the IV's used to encrypt a packet are not always different from each other.
Right?
I also understood that you need to add a dictionary-file for the aircrack-ng to be able to crack a WPA with a pre-shared-key.
But what is the point of using a dictionary? If you use that, why would you bother collecting packets? Using a dictionary is basically guessing the encryption-key isn't it?

---

### Post by Neosano on 2010-05-01
uh...
You must collect IV's to crack WEP.
For cracking WAP you must get the handshake and use the dictionary to bruteforce the password from it.

---

