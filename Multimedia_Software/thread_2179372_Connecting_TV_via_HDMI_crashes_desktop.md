---
title: "Connecting TV via HDMI crashes desktop"
date: 2013-10-07
forum: Multimedia Software
---

### Post by tXtnhFp on 2013-10-07
I've got a 3 video card machine, all are nVidia cards, and in Windows I can use them in an integrated mode (using the single 9400m) or hybrid SLI (using the 260m cards as well).

This is what I get when I type 'lspci -nnk | grep -i vga -A3'
> 

02:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92M [GeForce GTX 260M] [10de:0618] (rev a2)
    Subsystem: Dell Device [1028:02a1]
    Kernel driver in use: nouveau
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92M [GeForce GTX 260M] [10de:0618] (rev a2)
    Subsystem: Dell Device [1028:02a1]
04:00.0 VGA compatible controller [0300]: NVIDIA Corporation C79 [GeForce 9400M G] [10de:0862] (rev b1)
    Subsystem: Dell Device [1028:02a1]
    Kernel driver in use: nouveau




I'm having real trouble installing the drivers for the video cards - I downloaded a script from ubuntuxtreme.com which ran through and deleted nouveau, but it only found the sole 9400M video card. After rebooting, although I'd selected the option to install the latest stable prop driver, my video driver is still nouveau, I've attempted to install the correct drivers for the 260Ms using this page [http://sixcolumns.com/t/nvidia-310-19-drivers-released-how-to-install-it-in-ubuntu-12-1012-04-2/](http://sixcolumns.com/t/nvidia-310-19-drivers-released-how-to-install-it-in-ubuntu-12-1012-04-2/) but certain commands further down don't work properly on my system.

The whole reason I'm trying this is that by connecting the HDMI cable and turning on the TV, the TV says 'unsupported signal format' and the laptop screen just goes black, removing the HDMI cable doesn't bring the picture back, and I have to to a hard reset of the machine.

Does anyone have any ideas?

Thanks!

---

