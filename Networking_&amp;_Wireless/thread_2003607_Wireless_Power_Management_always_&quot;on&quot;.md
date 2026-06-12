---
title: "Wireless Power Management always &quot;on&quot;"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by maureenc on 2012-06-14
Hi,

I have Ubuntu 10.4 on my desktop and 12.04 on my Toshiba AC100 netbook.

On the AC100 I noticed that the wireless signal had dropped by around 20% after I installed Precise (from scratch) so I started rummaging around to see what could be the problem. I came across some posts about Wireless Power Management.

On both devices the Wireless Power Management is always on at startup despite my best efforts and despite the fact that the desktop shouldn't need to have it's wireless power throttled anyway.... And I have no idea at all what is resetting it there.

I've followed every instruction I have found so far and, althoughsetting it "off" in Iwconfig  works for that session, it is always overridden at restart/resume etc.

I have modified the "wireless" file in etc/pm and pm-utils and tried setting up a command from the Startup Preferences (This utility doesn't seem to be working at all in 12.04 as login sound is switched off there too but mysteriously still sounds and setting screen brightness is reset again as well).  I also changed the Bit Rate to 54 in Iwconfig but this is also overridden.

I am using Gnome Fallback on the netbook but the same thing happens when I log in via Unity.

I can't figure out which program/daemon is doing the override.

Does anyone have any ideas please?

---

