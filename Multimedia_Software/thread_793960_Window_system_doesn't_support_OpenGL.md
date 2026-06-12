---
title: "Window system doesn't support OpenGL"
date: 2008-05-14
forum: Multimedia Software
---

### Post by kaktux on 2008-05-14
after upgrading form Kubuntu 7.10 i have problems running everything (at least it seems to me like that) using OpenGL
This means for examples: Games like Supertuxkart, all the opengl screensavers and zattoo (which gives me the error message:"Window system doesn't support OpenGL" - thats why i think this could be the problem)

In Kubuntu 7.10 there was an option under
System-settings -> Advanced -> restricted drivers
where i had to mark the option for the graphic acceleration (hope this is the right word for that) to get zattoo to work.

Now on Kubuntu 8.10 this option is no longer available in the system settings (the option Restricted drivers ist not available at all) - so as i'm not that much an expert i don't know what to do...

if someone needs:
the graphic card is  dell standart (about 3 years old)
lspci gives:
```
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:09.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
01:0a.0 RF controller: Advanced Micro Devices [AMD] Am 1771 MBW [Alchemy] (rev 04)
02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
03:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

under system->settings -> Display -> Hardware
there is also the Nvidia GForce FX (Generic)

The graphic card driver should be the standard to - as i just did the update - nothing more on this. nvidia-glx-new is installed.

would be great if someone could give me a hint as i'm already tring to solve this for about 3 weeks - without success.

---

