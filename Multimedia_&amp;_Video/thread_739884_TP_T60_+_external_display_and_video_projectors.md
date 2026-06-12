---
title: "TP T60 + external display and video projectors"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by analyzer on 2008-03-30
Hi

My hardware is a Lenovo ThinkPad T60 with a integrated ATI Mobility Radeon X1400 graphic adapter. The internal 14.1” display supports a resolution up to 1440x1050. My external monitor is a Samsung SyncMaster 2232BW 22” connected over DVI. I use Gutsy Gibbon.

At my everyday work there are the following situations:
1. Working just with the laptop internal display (1440x1050)
2. Working just with the Samsung monitor (1680x1050), laptop display should be off
3. Working with a video projector (1280x1024) and laptop display (1440x1050)

Unfortunately I have major problems to configure these situations. By the way, I use the ATI fglrx driver and no compiz.

I tried to configure these situations with the displayconfig tool. Only situation one works. 
At situation two and three exists the following problems.
There is no signal at the video projector
I can just work with a resolution of 1440x1050 at the Samsung monitor, laptop display is on
After a reboot the GDM keyboard layout is set to the American layout instead of Swissgerman.
After a reboot sometimes is the resolution of 800x600 set

Could it be, that there is a bug in fglrx or xrandr ?  Probably can an other ThinkPad T60 user post the xorg.conf for some of these situations.

Output of fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)
```

Sorry for my language.

Thanks for your help.

---

