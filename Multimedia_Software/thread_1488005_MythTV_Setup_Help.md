---
title: "MythTV Setup Help"
date: 2010-05-19
forum: Multimedia Software
---

### Post by false_chicken on 2010-05-19
I installed the mythtv-frontend package but need some help configuring it. My lspci shows this:

Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

Is this tuner compatible? And if so what settings should I use?

Im on 10.04 Thanks.

---

### Post by WinterRain on 2010-05-19
Give us the output of
```
lspci
```

---

### Post by wyliecoyoteuk on 2010-05-19
You will need the back-end as well.
The front-end can be installed on the same pc or a different one on the same network (or more than one) but the back-end handles the TV card tuning etc.
The best thing is to install the Mythbuntu packages, they will configure it (mostly) for you.

Or, if you just want to watch the odd bit of TV, use VLC (MythTV is a really meant as a dedicated PVR/media centre install)

[http://ubuntuforums.org/showthread.php?t=1042777](http://ubuntuforums.org/showthread.php?t=1042777) may help.

---

### Post by false_chicken on 2010-05-19
lspci:

"00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9600 GSO] (rev a2)"

I can use vlc to open the device (/dev/video1) But the screen is just black. The device has multiple inputs. It has Coax, Composite and svideo inputs. I dont know how to switch between them. I see no option to do it. Using Vlc would be ideal for me because all I really want to do Is play my xbox with it.

---

### Post by WinterRain on 2010-05-19
See [this]("http://www.linuxtv.org/wiki/index.php/Saa713x_devices").

---

