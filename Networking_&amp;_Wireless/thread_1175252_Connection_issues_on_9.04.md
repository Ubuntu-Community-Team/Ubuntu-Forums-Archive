---
title: "Connection issues on 9.04"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by Sonicjet on 2009-05-31
HI,and thanks for looking,I am a new user to ubuntu and am loving the OS but i have one painful woe in this,I plug my ethernet cable into the back of the equipped comp.(HP pavilion, 756mb ram,intel  celron 1.7ghz factory everything except ram,2003 had a fully funtional win XP till 4 days ago) and the net. manager displays this wireless icon,not wired and no ping,no manual connection,it acts like my ethernet cable does not even exist,I am using the 8gb/s variant of comcast,an Motorola surfboard modem and a netgear wireless/wired router.

---

### Post by coffeeaddict22 on 2009-06-01
At a guess, your ethernet card has a hardware switch, and it's off.  Have a look on the side of the machine, or check the manual for a function key combo.  They can be turned off in the BIOS too; thats a power- saving idea if you never use it (and a real pain when you forget you did it too...)

Open a terminal, and type in ```
lspci -v
``` if that doesn't work; post back the output that relates to your network/ ethernet controller if it's there.

---

