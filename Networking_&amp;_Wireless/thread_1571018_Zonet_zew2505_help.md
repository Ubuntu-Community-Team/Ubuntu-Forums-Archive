---
title: "Zonet zew2505 help"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by pennyrao on 2010-09-09
Hello all,

I just installed Ubuntu 10.04 and am trying to get my Zonet zew2505  wireless usb to work right.  So far I have
-installed ndiswrapper from the Synaptic Package manager
-copied the netMw225.inf and MRVW225.sys to my download directory

 Then I did a sudo ndiswrapper -i netMw225.inf
                               ndiswrapper -l 

 I got:
netmw225 : driver installed
     device (1286:1FAB) present

Then I ran   sudo ndiswrapper -m

But after the reboot, computer still can not find the wireless device. 
Any ideas why? Thanks in advance.

---

