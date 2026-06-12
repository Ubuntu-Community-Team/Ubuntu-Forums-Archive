---
title: "problem with nvidia: coolbits should solve wine problem"
date: 2008-08-14
forum: Multimedia Software
---

### Post by asdir on 2008-08-14
I cannot get Coolbits to show under the nvidia x-server settings. The nvidia-driver I use is nvidia-glx (vers. 96.43.05).

I tried to install coolbits following the guide on [http://wiki.ubuntuusers.de/Overclocking#CoolBits]("this wiki"), but after doing that it still not show up under nvidia-settings (yes,I checked if the binary is in "")

Since the Hardy version was originally a RC, I tried to replace the driver with nvidia-glx-new, but that did not work. (I thought a newer driver might solve the problem)

The system is Hardy (updated from a RC) with GeForce3-ti200

The original problem for which I wanted to install Coolbits was a problem with wine that made Diablo II under wine use almost all my system resources, which, according to a forum article was due to my graphics card being too fast. To clock it down, I wanted to use Coolbits.

If any one of you has any idea on either of these problems, it would be much appreciated.

Thanks in advance

---

### Post by wd5gnr on 2008-08-15
I doubt that is going to help you.

However, despite the Nvidia documentation, it matters what section you have the option in. In my /etc/X11/xorg.conf I have a section for Screen 0:

Section "Screen"
   Identifier "Screen0"
   Device "Videocard0"
   Monitor "Monitor0"
    . . .   # more stuff here omitted
   Option "Coolbits" "1"


Works for me. Of course, you need to restart X (either log out and use the menu -- at least you can on the latest kdm or just hit Control+Alt+Backspace after saving anything you are working on).

---

### Post by fig_wright on 2008-08-15
I have the same problem and the same graphics card. The option is registered in the xorg log file:
> (II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Option "Coolbits" "1"


Some people seem to suggest that "legacy" cards wont work with Coolbits, and this link appears to say Coolbits is only available on GeForce FX, Quadro FX, and newer desktop GPUs:
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-d.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-d.html)
but coolbits works fine for me in Win XP, so I dont see why that would be a problem.

---

