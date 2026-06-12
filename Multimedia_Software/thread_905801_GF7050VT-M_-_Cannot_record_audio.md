---
title: "GF7050VT-M - Cannot record audio"
date: 2008-08-30
forum: Multimedia Software
---

### Post by George_T on 2008-08-30
[Hardy] I have a Core 2 Duo CPU on a ECS GF7050VT-M motherboard, and when I try to record from a microphone in Audacity I get no sound. I suspect it could be because of either a driver problem, or a mixer problem.

I started by trying to see whether it is a volume issue. I checked to see that all capture devices are unmuted - and they are. Also, I made sure that the volume is set to 100% in gnome-volume-control, which lists two possible capture devices: Capture ALSA PCM on Front (STAC92xx Analog) via DMA (Pulse Audio Mixer); and Capture Monitor Source of ALSA PCM on front via (STAC92xx) DMA (Pulse Audio Mixer).

The motherboard has an integrated audio chipset. I am not exactly sure what it is because of the following:

If I do a lspci, I get:
> 
00:00.0 Host bridge: nVidia Corporation Unknown device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7050/nForce 610i (rev a2)

However, when I use alsamixer, I get the following devices:

> HDA NVidia Sigmatel STAC9221 AT chip


Does this mean it's a NVidia MCP73 chip, or a Sigmatel chip?

Any ideas on how to get sound recording to work would be greatly appreciated.

Full alsa-info output: [http://www.alsa-project.org/db/?f=2dc290bbf62dced137daa799e0c17a967d9b4b3c]("http://www.alsa-project.org/db/?f=2dc290bbf62dced137daa799e0c17a967d9b4b3c")

---

