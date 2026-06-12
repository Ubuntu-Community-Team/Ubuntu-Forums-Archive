---
title: "Scrambled images"
date: 2008-07-01
forum: Mythbuntu
---

### Post by fcmartins on 2008-07-01
Hi,

I'm running Gutsy and MythTV 0.21 from gutsy-backports.

After I installed the latest 8.6 ATI fglrx driver (because I needed TV out) the image of MythTV got all scrambled. I can't see the menus, no configuration screens (both in mythfrontend and mythbackend) and no video.

I can (by trying around) access the menus, watch TV and recordings. It all works fine but everything looks scrambled, like the image was broken in small rectangles and spread all over the screen. 

My desktop is 1024x768, and I have tried 640x480 and 800x600 as well, to no avail. However, if I run mythfrontend with a smaller resolution, using the "--geometry" switch, everything looks perfectly, so I think it might have something to do with fullscreen mode.

---

### Post by dettrittus on 2008-08-05
Hi,

I have the exact same problem. Did you manage to solve it?

Config:
AMD Athlon 64 X2 5000+
ASUS M2A-VM (Radeon X1250)

Catalyst 8.7
Hardy

---

### Post by fcmartins on 2008-08-05
I found out that it works with 640x480 only, any other resolution will get scrambled.

Other applications, tvtime, mplayer, work just fine, the problem only affects MythTV with ATI drivers.

---

### Post by dettrittus on 2008-08-06
I tried a few thing. On my side, any resolution not fullscreen seems to work. I guess i'll have to mess around with window position/resolution to get it working on my tv.

thanks

---

