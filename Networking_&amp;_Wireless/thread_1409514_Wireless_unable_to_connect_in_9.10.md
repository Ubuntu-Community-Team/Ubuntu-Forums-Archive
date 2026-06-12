---
title: "Wireless unable to connect in 9.10"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by racie on 2010-02-17
Hey *buntu users, I've decide to go from Jaunty to Karmic with a fresh install.  Around the same time, my brother switched our wireless from WPA to WPA2.

The install worked smoothly and quickly, as usual, but when it came time to connect to the internet, problems arose.  When I try to connect to the wireless internet, it sits there a while trying to connect, but then I get a message saying "disconnected - you are now offline."  I can't connect via ethernet cable because I misplaced mine.

In terminal, when I type "lspci," I get:
```
Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

My card is actually an Atheros AR5007, which could be causing part of the problem.


Since I can't connect to the internet, is there anything I could download and put on a USB that could possibly fix this problem? Thanks! 

Oh, and also--it may take me a while to respond if I am to check something in Ubuntu, as I am dual-booting.  So please bear with me.

---

### Post by oneindelijk on 2010-02-17
maybe try wicd
[http://mirrors.kernel.org/ubuntu/pool/universe/w/wicd/wicd_1.6.1-3ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/w/wicd/wicd_1.6.1-3ubuntu1_all.deb)

---

### Post by oneindelijk on 2010-02-17
It also might be a problem described in this thread:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1846844.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1846844.html)
So maybe try changing the channel from the router to one that's less than 12.

---

### Post by lidex on 2010-02-17
You may need to go back to WPA1 or use a different driver compatible with WPA2. What is the make and model of your PC? meanwhile:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by racie on 2010-02-17
Thanks for your responses, but the problem resolved itself.  I found my ethernet cable, attatched it, and updated.  After the update, the wireless works fine.  :D

---

