---
title: "Cannot enable wifi on akoya P6624 (=Medion MD 98390)"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by MrHobbit on 2010-11-22
I am running Ubuntu 10.10, 64-bit on Akoya P6624 (also known as Medion MD98390 from Aldi) from the ubuntu live CD (I intend to replace windows7 by a normal ubuntu installation as soon as the wifi works properly).
The wifi adaptor is Realtek rtl8191SEvB (rev 10).
The problem is that I cannot enable/disable the wifi using the function keys (**Fn + F7**). 
When I press the key combination nothing happens. 
Also no messages on any log.
The only way I get it working is by enabling the "remember last wifi state" in the bios, then boot windows7 and enable wifi using Fn+F7 and then boot ubuntu (from the live CD in my case). 
From now on the wifi remains on, even after reboot.
If I need to turn it off (or on again in case it switches off for some reason), then I need to do the windows7 bypass again.
Of course this is not how it should work.
Does anybody have an idea how I can solve this issue ?

Kind regards.

---

### Post by jbart on 2010-12-05
Also running Ubuntu 10.10 on the same setup. You can fix it by changing your bios settings. 
There is an option to remember the LAST STATE of the wireless mode. Even the dual head
mode seems to work great. Only had problems when I did install the nvidia drivers. So I am
running on the default video card now. But I don't need fancy 3D stuff. 

If you re-install win 64 bit plain vanilla, you will even have the same problem. It only works
after installing specific launch manager tool (can be downloaded on p6624 support site).

---

### Post by cpmman on 2010-12-05
I had a MD96640 and left it in last state from W7.

Use the "rfkill" command to soft block the wifi.

"rfkill list" will tell you the mnemonic to use (e.g. "rfkill wifi") to block it.

---

