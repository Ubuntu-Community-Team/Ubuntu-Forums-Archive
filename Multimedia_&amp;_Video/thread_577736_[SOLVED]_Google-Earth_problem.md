---
title: "[SOLVED] Google-Earth problem"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by borobudur on 2007-10-16
I'm trying to install google-earth but it crashes when I start it after the installation. 

I thought it's the grafic driver, so I installed with the ENVY software the nvidia driver. But after that I had a resolution problem. I guess it wasn't the correct driver which got installed. 

Has anyone an idea what else I could try?

Here a plot of lspci
```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)

```

---

### Post by wolfen69 on 2007-10-16
try removing the nvidia driver, then reboot.
then, in terminal:
```
sudo apt-get install nvidia-glx
```

---

### Post by borobudur on 2008-03-01
With Gutsy Gibbon it works finally...

---

