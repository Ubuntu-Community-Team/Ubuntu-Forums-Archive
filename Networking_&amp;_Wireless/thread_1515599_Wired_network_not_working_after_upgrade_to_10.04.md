---
title: "Wired network not working after upgrade to 10.04"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by uberben on 2010-06-22
I recently upgraded to 10.04 and now my wired network no longer works. I am unsure if it worked at all since the upgrade as that computer is rarely used, but it was definitely working prior to the upgrade. It is some sort of Realtec card, I believe. Does anyone have any suggestions?

I'm running 32 bit 10.04 on a 2 GHz P4.

Thanks in advance.

---

### Post by uberben on 2010-06-22
Just to clarify, in the network icon in the upper right corner, it tells me that the network cable is unplugged, but it is definitely connected, and that cable in that port on the router works on other machines. The network card in the problematic computer even has little lights blink at me when i plug the network cable in.

---

### Post by uberben on 2010-06-22
False alarm. It turns out my internet is working fine, but the network manager doesn't think I have a connection. I thought my network was not working because I was trying to connect to shared files on a Windows 7 machine and it said that the network might be in error, at which point I noticed the icon. If anyone has tips for fixing the network manager, I would appreciate that.

---

### Post by Iowan on 2010-06-22
Unfortunately, losing networking is not a rare occurrence after upgrading to 10.04. From a terminal (Applications>Accessories>Terminal), check **sudo lshw -C network** to see if interface is recognized and has an alias (eth0) and associated driver.

---

