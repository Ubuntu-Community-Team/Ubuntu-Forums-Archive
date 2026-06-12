---
title: "Restore Network Manager 9.10"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2010-08-11
I installed WICD 1.6.2.2 through Synaptic Package Manager on this netbook because Network Manager is quirky. Unfortunately, with WICD installed, I can't get the little wireless lamp to switch on, and WICD can't find any wireless access points.:(

I reckon I have to go back to Network Manager -- how?

Or, some troubleshooting tips to get WICD to enable the wireless adapter?

---

### Post by Rocket J Squirrel on 2010-08-11
This fixed it:

sudo ifconfig wlan0 up
:KS

(I'd like to tag this as "solved" but can't find the button)

---

### Post by dineshs on 2010-08-11
click on thread tools

---

