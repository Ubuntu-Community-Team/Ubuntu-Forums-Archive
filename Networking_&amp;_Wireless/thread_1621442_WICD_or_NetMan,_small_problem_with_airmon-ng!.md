---
title: "WICD or NetMan, small problem with airmon-ng!"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by phazed on 2010-11-14
Hello,

I recently upgraded Ubuntu from 10.04 to 10.10 and I have a small annoyance that has popped up.

I'm using a Asus 1005HA Netbook with Ath9k drivers.

When using either WICD or Network Manager:

If I sudo airmon-ng start wlan0..... and get my mon0 everything is fine. However, what I have to do now is "sudo airmon-ng stop mon0" before I can use a Net Manager without locking the system up completely.

I didn't used to have to do this before the 10.10 upgrade. mon0 was able to coexist for as long as I wanted it to with no lockups. 

Also, the log files don't seem to show anything useful, the lock-up seems to REALLY kill everything, even log writing. 

I understand that it is probably good practice to kill mon0 before doing anything else, but I would really like it to work the way it was before! :-k

Perhaps a patched ath9k driver or something? I prefer not to go with the madwifi drivers as the ath9k go much faster for me.

[EDIT] Oh ya, all Terminals and air*-ng programs are stopped before connection attempt with WICD or NetMan, would simply like to keep mon0 "started".


Aaron
[www.AaronsPCSupport.com]("http://www.AaronsPCSupport.com")

---

