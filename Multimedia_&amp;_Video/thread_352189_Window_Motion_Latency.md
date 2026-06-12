---
title: "Window Motion Latency"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by stromb on 2007-02-03
Hi all,

Sorry for the lame title on the thread, but I'm not entirely sure how to describe this problem in words. But I'll give it a try...

I have a new Dell E521 and I have tried installing the last 3 Ubuntu releases including the recent Alpha 3 release of 7.04, but continue to have the same issue. Basically, whenever I open a window or attempt to drag it using the mouse cursor there seems to be an annoying delay in the window moving with the mouse. For instance, if I were to drag a window from the top-left to the bottom-right of the monitor, there would be about a 3 second delay before it moved - sometimes it won't even move until I let go of the mouse button. Also, when the window does move, it doesn't "drag", it actually appears to load from top to bottom (slowly) wherever I dragged it to without giving the traditional "drag" visual effect. The same page/window loading latency also happens when using the scroll-wheel on the mouse when viewing webpages.

The problem seems to specific to something in *buntu distros as I've also tried Kubuntu and Xubuntu just to test. I also *didn't* have the same problem when I tested Debian 4.0-RC1 or gNewsense 1.0.

Has anyone else had this problem or can offer any advice? I thought I would see if this was a simple fix before opening a bug report. 

Thanks!

```
ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem
```

---

### Post by maxamillion on 2007-02-03
I don't know the specs on your video card, but I assume you have a nvidia card and it sounds like the installer loaded the open source "nv" driver when you need to install the nvidia-glx package and edit it to "nvidia" in xorg.conf ....

How-To for this: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

Hope that helps .... if not, post back because it could possibly something other than the video card, that is just the first thing that came to mind.

---

### Post by stromb on 2007-02-04
Thanks maxamillion! I followed the guide and and everything works fine now (with the exception of 1680x1050 being displayed correctly, but I can live with 1280x1024 :)).

Is there some particular reason this isn't default driver? Or is my situation just a rare case/bug?

Thanks again...as usual, the Ubuntu community shines bright!

---

