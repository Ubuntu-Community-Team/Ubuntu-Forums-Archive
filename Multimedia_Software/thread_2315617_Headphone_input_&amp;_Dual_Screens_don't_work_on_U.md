---
title: "Headphone input &amp; Dual Screens don't work on Ubuntu 15.10"
date: 2016-03-01
forum: Multimedia Software
---

### Post by Pryzm on 2016-03-01
Hello,

After a [hard install of dual-boot Win10/Ubuntu on my laptop Alienware-15-R2]("http://ubuntuforums.org/showthread.php?t=2313054"), I noticed some problems :

[SIZE=4]_**Sound problem**_[/SIZE]

The speakers works fine on the laptop in Ubuntu/Win10, but when I plug Headphone on Jack Input, nothing happened in Ubuntu (the speakers continue to play sounds) but it works well in Win10. I installed AlsaMixer and switch all the devices "on" but it didn't work. Here is my alsa report : [http://www.alsa-project.org/db/?f=274e06e543eb0bd1856f633ae2850e64ee5b78d3](http://www.alsa-project.org/db/?f=274e06e543eb0bd1856f633ae2850e64ee5b78d3)

[SIZE=4]_**Dual Screen problem**_[/SIZE]

Same issue with my other screen which is plugged in HDMI : it works fine on Win10 but there some problems on Ubuntu. I have 2 graphics card (Intel and Nvidia) so I installed "Nvidia Prime" which permit to switch over the cards. The HDMI output not working (nothing happened : "cable not connected" on the screen even is plugged !) on Intel Graphics and works on Nvidia card (maybe because HDMI output is on Nvidia card ?). But with Nvidia, I have troubles because when I try to get a dual screen, the desktop seems to appear in the two screens with panning. I tried to desactivate panning but it didn't work. I also try another monitor, it's the same issue.

The "same display" on both monitors is good (as good as one monitor intern or extern solo), but both monitors on "extended desktop" mode don't work.

Here is my xrandr when Nividia is "on" and the output only on the extern monitor :
```

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     60.00*+  59.94    50.00    60.05    60.00    50.04  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       59.94    59.93  
eDP-1-0 connected
   1920x1080     60.02 +  59.93    48.03  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
DisplayPort-1-0 disconnected
HDMI-1-0 disconnected
DisplayPort-1-1 disconnected
HDMI-1-1 disconnected
  1280x1024 (0x4f) 108.000MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1440x900 (0x50) 106.500MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1024x768 (0x56) 65.000MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x5d) 40.000MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x5e) 36.000MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x66) 25.175MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz

```

Here is the xrandr where Nvidia is "on" and both screens are "on" :
```

Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm panning 3840x1080+0+0
   1920x1080     60.00*+  59.94    50.00    60.05    60.00    50.04  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       59.94    59.93  
eDP-1-0 connected 1920x1080+1920+0 344mm x 194mm
   1920x1080     60.02*+  59.93    48.03  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
DisplayPort-1-0 disconnected
HDMI-1-0 disconnected
DisplayPort-1-1 disconnected
HDMI-1-1 disconnected
  1280x1024 (0x4f) 108.000MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1440x900 (0x50) 106.500MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1024x768 (0x56) 65.000MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x5d) 40.000MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x5e) 36.000MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x66) 25.175MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz

```


Can someone help me to fix those issues please ? I don't know what to do... :/

Thanks in advance, 

Pryzm.

---

### Post by Pryzm on 2016-03-14
Does someone can help me please ? :-(
At least I need two screens for my work, it would be great if someone can help me to configure xrandr to do that.

Thanks in advance, 

Pryzm.

---

### Post by The Cog on 2016-03-14
There is a GUI version of **xrandr[/B ]called [B]arandr** which is in the repositories. That's much easier to use.

I haven't seen a problem where the screens won't show separate images for years. But then, I use Xubuntu. So perhaps there's an issue with Ubuntu although I would expect to see more complaints if that were the case. Are you sure the video card has enough memory to do two separate desktops at high res? I had a laptop that couldn't perhaps ten years ago.

---

### Post by tony116 on 2016-03-28
> **Pryzm said:**
> Does someone can help me please ? :-(
At least I need two screens for my work, it would be great if someone can help me to configure xrandr to do that.

Thanks in advance, 

Pryzm.

Pryzm,

I have the same exact laptop and still have not figured out how to get headphones working. I haven't tested dual monitors yet but am on xubuntu 14.04-4 and will give it a try to report my findings. 

Question: Can your suspend and resume your laptop with no problems? 
If I install xubuntu 15.10 it breaks my suspend function IE seems graphics driver crashes and will not log back into session.

---

