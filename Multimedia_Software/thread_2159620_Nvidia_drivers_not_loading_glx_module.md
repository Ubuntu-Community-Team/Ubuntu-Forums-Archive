---
title: "Nvidia drivers not loading glx module"
date: 2013-07-03
forum: Multimedia Software
---

### Post by DK32 on 2013-07-03
Hey,

I'm writing a simple game using SDL and opengl.  The program was behaving weird on my computer, but worked perfectly on a different computer.  An experienced programmer and linux user suggested I may need to change which drivers I was using, so I attempted to install the proprietary Nvidia drivers.  Now when I run the program, it says "couldn't load matching glx visual".  I've been reading forums trying different solutions for the past few days to no avail.  Reinstalling the nvidia drivers, running nvidia-xconfig, deleting xorg.conf and recreating it have done nothing.  Also, when I run Xorg -configure in root recovery mode, it fails, saying "number of created screens doesn't match detected devices", or something to that effect.  I've even tried removing the nouveau drivers, even though most sites have said you should be able to leave them installed.

Here is the output from lspci:
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [NVS 5400M] (rev a1)
02:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 08)
02:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)
```

Here is the output from glxinfo:
```
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig


Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
```

---

### Post by DK32 on 2013-07-03
Also, the additional drivers page is not detecting the nvidia drivers at all.

---

### Post by Yellow Pasque on 2013-07-04
You don't have an nvidia GPU. You have intel/nvidia hybrid graphics (aka Optimus).
You need to purge the nvidia drivers you installed and get your system back to a working state. After that, see: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

> Also, the additional drivers page is not detecting the nvidia drivers at all. 
That's correct. Installing nvidia drivers directly borks the intel GPU (as you've discovered).

---

### Post by DK32 on 2013-07-05
Thank you very much!  That got rid of the glx error and everything seems to be running fine.  Now I just have to fix whatever was wrong in my program that started all of this .  This is the first time I've ever seen the same program (well, one this simple anyway) NOT do the exact same thing every time it runs, but that's another problem haha.  ](*,)

---

