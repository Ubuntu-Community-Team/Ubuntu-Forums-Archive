---
title: "Wired Internet Not Always Working"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by Nilladar on 2012-11-29
Im currently running ubuntu 12.10 x64 and sometimes I have no incoming traffic from the internet. To resolve the problem I have to disable and then enable networking multiple times. After a couple of times everything starts to work fine and I dont have any problems until logout.

I found this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836) didnt try it, but im guessing it is not relevant any longer?

```
lspci
00:00.0 Host bridge: NVIDIA Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP55 SMBus (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: NVIDIA Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: NVIDIA Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: NVIDIA Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a3)
00:12.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a3)
00:13.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch (rev a2)
02:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch (rev a2)
02:02.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch (rev a2)
03:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 9800 GTX] (rev a2)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
```

---

