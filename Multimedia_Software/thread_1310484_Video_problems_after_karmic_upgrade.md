---
title: "Video problems after karmic upgrade"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Ch33zm0ng3r on 2009-11-01
I just upgraded to karmic this evening and now all video playback displays inverted colors and there is no sound.  Playback through Amarok and Rythmbox works just fine.  Is anyone else experiencing this problem and is there a known solution? 

Thanks


Info: 

I am using the NVIDA drivers version 185. 

lspci output: 
```
00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82G35 Express PCI Express Root Port (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
05:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

```

---

### Post by Ch33zm0ng3r on 2009-11-01
The color issue was easily fixed.  There is a hue setting in the video player that was way off by default for some reason.  The sound is still an issue.

---

