---
title: "Slow internet speed after mainboard replace"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by openware on 2010-02-08
I replaced only my mainbord and cpu and Ubuntu 9.10 boot just fine. The only issue that I have is that my connection speed dropped from 10Mb to 3Mb. I try the connection on my laptop and it is fine 10Mb, so the problem is with the PC. What else to try before reinstall Ubuntu as a final step? 
Thanks for your time!

---

### Post by openware on 2010-02-08
I just found this line in my dmesg:
[  598.579020] eth0: link up, 10Mbps, half-duplex, lpa 0x0000

so I execute:
sudo mii-tool eth0 -F 100baseTx-FD
sudo mii-tool eth0 
give me:
eth0: 100 Mbit, full duplex, link ok

And speed is now ok : ))
I just wonder why that happen?

---

### Post by Grenage on 2010-02-08
Auto negotiation decided that the connection couldn't handle much more.  I'd check the cabling, bad auto negotiation is indicative of crap wiring.

---

### Post by elliotbeken on 2010-02-08
this is always a question i wanted to ask

i know when you install windows XP of one system to cant really take the hard drive out and put it in another system  that is totally different and expect it to work

but when i have done this with ubuntu it does not seem to matter is this the case ?

---

