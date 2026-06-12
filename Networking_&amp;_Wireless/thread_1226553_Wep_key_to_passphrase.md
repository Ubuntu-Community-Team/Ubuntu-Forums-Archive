---
title: "Wep key to passphrase"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by l951b951 on 2009-07-29
At my office today, I helped set up a friend's wireless.  Our network has a wep key.  At my house I use wep also, and generated the key using a personal word as my passphrase that generated my wep key.  

I got curious today, is there a way to reverse the process?  I have my office's wep key, is there a package I can install to enter the key and see the passphrase that spawned it (if any)?

---

### Post by hamstersquasher on 2009-07-29
The passphrase is only used to *generate* a wep key that is then combined with a 24-bit initialization vector to create a sudo-random series of bits that are then XOR'd with the data you transmit over the air.  You can use programs like aircrack which can recover the wep key but I don't know if you can ever recover the original passphrase or not.  This may also be considered a moot point though since you only need the wep key to decrypt the communications.

---

