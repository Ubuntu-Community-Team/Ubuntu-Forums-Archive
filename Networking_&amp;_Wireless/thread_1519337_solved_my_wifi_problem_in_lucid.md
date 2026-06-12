---
title: "solved my wifi problem in lucid"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by v1nsai on 2010-06-28
I just put Ubuntu on my mom's Dell Inspiron 1545 with a Broadcom 4312 Wifi card in it (run lshw -C network to see what kind of card you have) and for a while was unable to get it to use the wifi at all.  lshw reported that it was disabled, and no command would get it to say otherwise.

I was switching drivers back and forth in System > Administration > Hardware Drivers when I noticed that my wifi suddenly saw all the networks around me!  I connected and sent out some pings, all was well.  After rebooting, it went away, and wifi card was again undetected.  I opened Hardware Drivers again, and was asked to unlock my keyring.  As soon as I did, the wifi connected and all networks were visible.

I smell a permissions bug in network-manager....seems to be "fixed" as long as you unlock your keyring.  Anyone know how to force this?  I can only get it to ask me to unlock by going to Hardware Drivers, I'm sure there's a better way though.

Anyway hope this helps someone, I found a lot of people having this problem in karmic and lucid but not many solutions.

---

