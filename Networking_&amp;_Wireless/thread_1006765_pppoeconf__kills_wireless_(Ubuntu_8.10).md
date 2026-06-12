---
title: "pppoeconf  kills wireless (Ubuntu 8.10)"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by sonofagun on 2008-12-09
Hi and thanks in advance to anyone that can help me with this issue.

My Issue:

I installed Ubuntu 8.10 which went fine. I am using a D-Link wireless card with RALink chipset which was recognised by the install and was a breeze to setup.
At this point I can reboot Ubuntu and wireless/network manager icon in the taskbar comes up every time.

Once I run pppoeconf I successfully get an internet connection which is great.

Once I do a restart the network manager icon in the taskbar no longer appears and networks are no longer availble, this includes my wired network.

Important to note that I haven't applied any updates or installed any additional software at this point.

I am new to Ubuntu and like its simplicity, it would be nice to get this working, so any help appreciated.

Cheers
Steve

---

### Post by der_vegi on 2009-04-06
pppoeconf writes some changes to /etc/network/interfaces that network-manager does not manage the device any more. Just uncomment all lines containing the name of your wireless deivice (typically 'wlan0') by putting a '#' in front. After reboot, network-manager should talk to your device again.

---

### Post by FLURPY on 2009-08-16
thanks for the tip.
It works for me, but it is a bit of a hassle to edit interfaces by removing the lines pppoeconf added, then reboot and rerun pppoeconf everytime I want to go online.

Is there not a way to prevent pppoeconf from changing interfaces and save me this hassle?

Any help will be appreciated

---

