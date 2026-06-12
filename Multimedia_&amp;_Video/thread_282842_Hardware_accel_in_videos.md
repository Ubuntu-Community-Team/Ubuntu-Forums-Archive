---
title: "Hardware accel in videos"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by Kameli on 2006-10-23
*Hello!*
[B]
Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6600 GT]"
Driver "nvidia"
Option "VideoOverlay" "on"
Option "NoLogo" "1"
BusID "PCI:1:0:0"
EndSection
[/B]
I have those in my xorg.conf but still i can't get hardware accel in videos, my 6600GT is very great card and it has several nice enhanced video, nice features and nice quality features. But i can't use them because my very naughty Xorg.0.log says some naughty things to me, like
[B]
(WW) NVIDIA(0): Option "VideoOverlay" is not used
[/B]
](*,) ](*,) ](*,)](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by John.Michael.Kane on 2006-10-23
What guide did you use to install your drivers?

You may need to reinstall them.
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

---

### Post by Kameli on 2006-10-24
I just typed sudo apt-get install nvidia-glx for install them. :)

---

### Post by CatKiller on 2006-10-24
I don't know where you got the idea of using that option from - possibly from someone's config that was using a different driver for a different make of card? But [VideoOverlay is not used]("http://download.nvidia.com/XFree86/Linux-x86/1.0-9625/README/appendix-d.html"). It's not an option. Pick a different one instead.

---

