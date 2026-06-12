---
title: "Problem with 12.10, only one resolution, nvidia"
date: 2012-10-26
forum: Multimedia Software
---

### Post by Jitsumi on 2012-10-26
Hi everybody!

I migrated from 12.04 to the 12.10 not a long time ago, and since, I cannot change my resolution. I have only one, the native one. I tried to had manually the resolution in xorg.conf, but it does not help...

It a serious problem for making presentation in dual screnn, and also plying games...

My graphics card is a nvidia quadro FX 2800M znd I'm using the driver 304.43 .

Do you have any idea how I can solve this problem? At least how may i force the resolution?

Thanks!

---

### Post by FarJumper on 2012-10-30
The same for me after upgrading to 12.10.

kernel: 3.5.0-17-generic
nvidia-current: 304.51.really.304.43-0ubuntu1

Bot xrandr and nvidia-settings say that there is only one mode available.

xxxx@xxxxlaptop:~$ xrandr
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1366x768+0+0 (normal left inverted right x axis y axis) 270mm x 150mm
   1366x768       60.0*+
HDMI-0 disconnected (normal left inverted right x axis y axis)

---

### Post by FarJumper on 2012-10-31
This link is useful:
[https://bbs.archlinux.org/viewtopic.php?id=145671](https://bbs.archlinux.org/viewtopic.php?id=145671)

---

### Post by uwt on 2012-11-17
> **FarJumper said:**
> This link is useful:
[https://bbs.archlinux.org/viewtopic.php?id=145671](https://bbs.archlinux.org/viewtopic.php?id=145671)
Informative, yes, as there seems to be some issue with the way that the nVidia proprietary driver exposes non-native resolutions? But, sadly, not so helpful except for the case of WINE, where the workaround was to use an older version until things get fixed.

Still trying to figure out how to force lower resolutions on the LCD panel in Ubuntu in general, since I need to mirror the screen with an external projector (1024x768).

Wonder if the workaround at [http://askubuntu.com/questions/202766/only-one-resolution-available-in-xorg-conf](http://askubuntu.com/questions/202766/only-one-resolution-available-in-xorg-conf) will work for me. Have to try it and report back later.

---

### Post by lcampagn on 2013-01-25
Same problem for me. One solution is to use nouveau drivers instead of nVidia's (this is really just exchanging one set of bugs for another).

Bug report here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1105392](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1105392)

Possible solution here?
[http://ubuntuforums.org/showthread.php?t=2072181](http://ubuntuforums.org/showthread.php?t=2072181)  **Edit:** This causes other resolutions to be available (xrandr lists them) but they are not usable; the screen simply goes black if you try.

I also tried installing the latest driver directly from nVidia (310.32) but this has exactly the same issue.

There is a discussion about the bug on the nVidia forums here: [https://devtalk.nvidia.com/default/topic/526439/linux/black-screen-after-resollution-change/](https://devtalk.nvidia.com/default/topic/526439/linux/black-screen-after-resollution-change/)

---

### Post by lcampagn on 2013-02-07
Here's a better thread discussing the problem:
[https://devtalk.nvidia.com/default/topic/525287/linux/non-native-resolutions-not-available-in-3xx-drivers-on-8700m-gt/](https://devtalk.nvidia.com/default/topic/525287/linux/non-native-resolutions-not-available-in-3xx-drivers-on-8700m-gt/)

It appears that nVidia is aware of and has no intention to correct the issue, so a workaround from ubuntu or the xorg folks may be the only solution..

I would just recommend the nouveau driver if it weren't for the [overheating issues (#858265)]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/858265").

---

