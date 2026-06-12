---
title: "Help Alsa"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by brandoncolorado on 2007-03-03
Hi Everyone,

Let me start by saying that I would really appreciate if someone could help me out with this problem.  I haven't had sound since I got my laptop in August, and I am going crazy trying to fix this problem.

That said, here is an overview of my problem.

I run a Gateway MX3414 laptop with a Sigmatel Stac92xx chipset.
I have NO sound.  No beeps nothing.
I have been monitoring changes to ALSA drivers and it seems that 1.0.14rc2 may have a fix for my card, but it says Sigmatel Stac9250 series, so I'm guessing it won't work.

Anyways,  

I have read many, many forum posts, and from what I have read, I thought it would be good to install 1.0.14rc2 ALSA Drivers.

I downloaded, ./configure, make, make install.
I also added a line to modprobe.d from another forum.

Now I still have no sound, and when I click on the volume icon my computer freezes.  
When I go to preferences---->sound, it says sigmatel stac92xx (disconnected).

PLEASE HELP!!!!  I love Ubuntu, and I love music and videos, and I would love to have sound working.:confused: :confused: :confused: :confused: :confused: :confused: :confused: 

```
lbrandon@brandon-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8185 (rev 20)
brandon@brandon-laptop:~$ 
```

---

