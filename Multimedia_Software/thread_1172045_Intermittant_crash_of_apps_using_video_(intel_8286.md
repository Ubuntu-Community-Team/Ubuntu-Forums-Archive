---
title: "Intermittant crash of apps using video (intel 82865G and driver 2.4)"
date: 2009-05-28
forum: Multimedia Software
---

### Post by jrav on 2009-05-28
on jaunty, i was using below intel chipset and default jaunty video drivers, which gave me blue screens when i tried watching video. so then i tried optimizing the intel chipset ([http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)), which made frequent crashes happen. so then i reinstalled jaunty, and reverted to driver 2.4 ([https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)) which universally (at least for 82865G) seems to be the only solution currently.

but now i get random (ie. once every 30 minutes) crashes of apps using video (watching flash in FF, or mpg in totem movie player), and occasionally entire crashing of X (requiring me to relog on). i was wondering how to find and view some logs that might describe what's going on. thanks for all the help!

lspci -nn | grep VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

uname -r
2.6.28-11-generic

---

### Post by jrav on 2009-06-01
bump for anyone else with this issue? i'm using this as a htpc, and it's literally become somewhat of a showstopper-i used this comp when xp came out, and i don't want to go back, but the crashes make ubuntu look alot worse.

as an aside, i'm using ubun w/ another setup using nvidia chipset and sempron 3000 and don't seem to have these issues. i guess some hardware, even older ones, aren't right w/ linux.

---

