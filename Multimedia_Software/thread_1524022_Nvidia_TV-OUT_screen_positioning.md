---
title: "Nvidia TV-OUT screen positioning"
date: 2010-07-04
forum: Multimedia Software
---

### Post by sammael666 on 2010-07-04
hello,

i have a problem with my tv-out output under linux. the screen on tv appears at first "zoomed" and "shifted" to the left. the "zoomed" part can be remedied by playing with the TVOverscan value in nvidia-settings, and i managed to find the right value in order to have screen centered vertically. however there is no setting (or maybe rather i was unable to find one) to "shift" the screen left or right. i would need to move the tv output about 10cm to right because as it is now i have 10 cm cut off on the left side and 10cm of black space on the right side.

i remember having this problem back in the day when even the TVOverscan value wasn't working with then current nvidia drivers for me, i am very pleased to see it working in this last release, however the ability to move the screen around is still missing. it is implemented in windows version of the drivers though so i was hoping i maybe only overlooked the setting.

so my question is: is there any setting i could put into xorg.conf or .nvidia-settings.rc similar in effect to TVOverscan but not affecting the "zoom" of screen but rather its position?

hw in question is:
intel Q9450 cpu
asus p5n-t deluxe mobo
2x nvidia 9800GT gfx
1280x1024@75 primary lcd monitor
1024x768@50 secondary crt tv-out PAL-I connected with S-VIDEO
ubuntu 10.04 64bit

thanks a lot for every suggestion!

---

### Post by sammael666 on 2010-07-06
bump:confused:

---

