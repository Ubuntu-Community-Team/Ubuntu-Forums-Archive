---
title: "Intel Pro/Wireless 3945ABG stopped working"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by piojominero on 2011-08-11
HI:

I'm new to linux. I've just installed Ubuntu 11.04. It has all been going ok, but the wireless just stopped working all of a sudden. The indicator light turned off and when I tried to turn it back on (Fn+F2) nothing happens. Sometimes, when I restart the computer, the wireless might work; but if the signal is lost the LED on my laptop turns off and I cannot reconnect. Also, in these strange cases that the wireless works when I restart I can manually turn it off (Fn+F2), but nothing happens when I try to switch it back on.

In the menu on the upper right corner I see 'Enable Networking' is checked, but 'Enable Wireless' cannot be modified.

I have a Dell Inspiron 6400 and the wireless device is an Intel Pro/Wireless 3945ABG.
I have tried to follow some of the threads on this forum on similar cases, but the ones that were comprehensible to me did not work (or I actually might not have understood them either).


Running
rfkill list all
delivers the following:

0: dell-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no


Please help!

---

### Post by pytheas22 on 2011-08-11
I have a similar issue with an iwl5xxx (I forget the exact chipset) on a Latitude 2100 netbook.  If I turn of the wireless using Fn+F2, I can't reenable it until I again toggle Fn+F2 and then type in a terminal "sudo rfkill unblock all"  This wasn't an issue in earlier releases; it seems to be a bug in Ubuntu 11.04.  One of these days I just might find the time to see if it's been reported :)

Any chance typing that terminal command (after reenabling the wireless by pressing Fn+F2) solves the issues for you?

---

