---
title: "sound on nvidia onboard card"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by BerlinOliver on 2006-07-17
Hi,

I am using a M2NPV-VM motherboard. It's an nVidia GeForce 6150 chipset. lspci says the following:
```


0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
0000:00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AM[CODE]
```D] K8 [Athlon64/Opteron] Miscellaneous Control
0000:04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:04:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:04:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
olli@Venusfalle:~$    [/CODE]

After I log in Kubuntu Drapper 64 my sound starts beeping loud. normal sound is quiet. nVidia driver is instaled. For that I used the thread by tseliot. Can anybody please help me?

---

