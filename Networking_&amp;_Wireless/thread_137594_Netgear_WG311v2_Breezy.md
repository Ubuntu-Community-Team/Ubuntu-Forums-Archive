---
title: "Netgear WG311v2 Breezy"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by metalox on 2006-02-28
This Netgear WG311v2 wireless LAN card with Teaxas Instuments ACX 111 Chipset used to work (sometimes) in Hoary. Now it doesn't work at all in Breezy. :( 

I have setup ndiswrapper using the Windows XP driver:

$ sudo ndiswrapper -l
Installed ndis drivers:
wg311v2 driver present, hardware present

$ sudo ndiswrapper -m
modprobe config already contains alias directive

$ dmesg | grep ndiswrapper
ndiswrapper version 1.1 loaded (preempt=no,smp=no)

But, I can't "see" my wireless router:

$ iwlist wlan0 scan
wlan0     No scan results

I read somewhere that I should remove the ACX modules:

"... Remove the ACX driver from /lib/modules/etc. etc. and run depmod -a ..."

But how to do this? Which files? Do I just delete the files and then run depmod -a ?

The router is working and has all security switched off for testing. The router works fine with other machines so I am sure that the router is not the problem.

Any help much appreciated.

---

