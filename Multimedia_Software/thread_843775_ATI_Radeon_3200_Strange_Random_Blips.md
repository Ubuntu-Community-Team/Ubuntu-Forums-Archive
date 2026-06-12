---
title: "ATI Radeon 3200 Strange Random Blips"
date: 2008-06-28
forum: Multimedia Software
---

### Post by dbsoundman on 2008-06-28
I just today built this computer, with an AMD Athlon 64 X2 2.7GHz processor, and an ASUS M3A78 mobo. I installed Ubuntu 8.04 on the system. The mobo has  built-in Radeon HD 3200 graphics. In general, everything works fine: with the ATI driver installed (done automatically by Ubuntu) I get the right resolution and all that, but I seem to be getting an odd issue with random dashes showing up around the screen. Occasionally I'll get really strange "subliminal message" images that just randomly come up when I open a program, then disappear just as rapidly as they appeared. I probably picked yet another graphics card that isn't well supported in Ubuntu, but I'm curious if anyone else has this problem and/or knows how I can fix it. I have a feeling it may be as simple as a setting in the xserver, but I realize with 8.04 that whole thing has changed so I wanted to ask first.

Thanks,
Dan

---

### Post by dbsoundman on 2008-06-28
One update: I just turned off desktop effects, and the blips appear to be gone. Anyone know why this happens though?

-Dan

---

### Post by markbuntu on 2008-06-28
I have that problem with my i386Hardy in firefox and a few other apps when compiz is running, not on the desktop but only in the apps. I have no problems like that at all with my amd64 install. Both are on the same machine on identical hard drives with a ATI Radeon HD3650 using the 8.6 driver from ATI. I did not have this problem with the 8.5 driver from ATI.

Go to there site and file a bug report.

I really think that until this compiz issue is fixed, the ATI drivers will continue to have wierd problems like this. fewer and fewer with eash release for sure but still... 

Rest assured though, the ati developers are well aware of this and are trying hard to fix it but it can be a difficult and time consuming thing to change 20 or 30 different drivers when they need extensive rewriting.

---

### Post by dbsoundman on 2008-06-28
I should report it at the ATI site? How do I find out which version I have (ex. 8.5 or 8.6)?

Thanks,
Dan

---

### Post by markbuntu on 2008-06-28
Catalyst Control Center has that in the information screen. The 8.6 driver is actually 8.50.3 in my info screen though I am sure I installed 8.50.1. Go figure.

If you are using the 8.5 driver it will be listed as 8.49.7 or something and the 8.4 driver is listed as 8.43.7 or something. Anyway,they will figure it out.

---

