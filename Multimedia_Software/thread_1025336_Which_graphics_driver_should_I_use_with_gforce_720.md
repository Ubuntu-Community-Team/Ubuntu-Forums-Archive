---
title: "Which graphics driver should I use with gforce 7200gs"
date: 2008-12-30
forum: Multimedia Software
---

### Post by sofasurfer on 2008-12-30
Running Hadry 8.10 (Intrepid)
Graphics card = Nvidia gforce 7200GS

When I go to system>preferences>appearances>visual effects, I click on "extra" effects and the list of possible drivers is displayed for just a split second before disappearing, then I see "desktop effects could not be enabled".

In Hardy 8.04 I ran the "nvidia glx" (no number) driver as far as I remember and I had extra effects working. In 8.10 there is no "nvidia glx" driver available in synaptic, only nvidia glx 177, 173, 73, 171, eic.

Which driver should I use?

---

### Post by sofasurfer on 2008-12-30
I tried 173 and 177(recommended) and the computer wants to start in low graphics mode until I tell it to use default configuration.

I need help getting advanced desktop effects to work. I need to no what driver to use.

Or heres a thought...
Do how I know if my graphics card is enabled or if I am using the video chip on the motherboard (gforce 6100, nforce 405). 

Heres my lspci output...
```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
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
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
01:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)


```

---

### Post by overdrank on 2008-12-30
Hi and it would appear that your motherboard is using the nvidia 7200. After installing the nvidia drivers have you tried using the xfix option by booting into recovery mode. 
Moved to Multimedia & Video  :)

---

