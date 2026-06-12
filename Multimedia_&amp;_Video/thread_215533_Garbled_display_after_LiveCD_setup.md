---
title: "Garbled display after LiveCD setup"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by Katryx on 2006-07-14
**Hardware**
------------
Motherboard: MSI K8N Neo4-F
Processor: AMD Athlon 64 3800+
Graphics: Nvidia GeForce 6600 GT (PCI Express)
Monitor: ViewSonic VA720 (17" LCD)
RAM: 1GB

**Ubuntu:** Dapper Drake 6.06, 64-bit version

I downloaded the LiveCD of the above Ubuntu version, and booted with it.  It got through all the automatic setup process with no problems.  Then when it would've switched to loading desktop (I think), the screen became covered in a nasty vertical-bars pattern of various colours.  There was nothing I could do except restart the computer using the button on the tower.

My question is, in short: why? :-k 

It looked like some kind of graphics glitch / incompatibility / non-recognition, maybe?

---

### Post by dan_kent on 2006-07-14
I'm sure why this happens but it has happened a few times me as well. Normally though you just reboot and everything works fine.
The other thing you try is booting the live cd in safe graphics mode - I always do this now as i find it works better with my nvidia card.

If you're still getting garbled graphics on reboot then you can reconfigure your xserver from the command prompt.

Dan

---

### Post by Katryx on 2006-07-14
Thank you, the safe graphics mode worked. :)

---

