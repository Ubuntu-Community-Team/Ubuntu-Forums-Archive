---
title: "Master Mode for LP-PHY Broadcom 4312?"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by N4RPS on 2011-09-01
Hello, all!
 
I was able to get Ubuntu 11.04 working with the STA driver, but apparently, it doesn't support master mode. I've heard that the b43 driver will, but it won't run on an LP-PHY adapter.
 
Does the b43lpphy driver support master mode, and if so, can I use it, in lieu of the STA driver, to give me the master mode option I seem to need to run the card as a wireless access point?
 
Any help you can provide will be appreciated. :confused:
 
73 DE N4RPS
Rob

---

### Post by northd_tech on 2011-09-01
From my brief searches, it doesn't sound excessively hopeful and/or easy:

> B**roadcom 43xx cards (bcm43xx.ko)** Broadcom  cards support master mode using the reverse-engineered kernel driver.  You need to enable (or make as a module) the Softmac wireless extensions  and BCM43xx wireless driver. 

[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

[B]Broadcom 4312 Master Mode?
[http://ubuntuforums.org/showthread.php?t=1044666](http://ubuntuforums.org/showthread.php?t=1044666)
[/B]

---

### Post by N4RPS on 2011-10-05
My thanks to you, for running this rabbit for me. 

It sounds like I'm going to have to wait until I learn more before I can put together something like that. Once I do, I'll release it to help the others in my situation. 


73 DE N4RPS
Rob

---

