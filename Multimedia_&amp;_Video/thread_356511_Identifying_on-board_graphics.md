---
title: "Identifying on-board graphics"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by IntoTheLight on 2007-02-08
I'm pretty new to this, and need help identifying my on-board graphics, so I know what drivers to use (after which I will undoubtedly be asking for help in getting them to work).  

I know that I have nVidea (it says so on the front of my case, and I have looked right at the chip), but nothing more.  It's a relatively new computer from Gateway, AMD Athlon 64x2, Windows Media Center, Vista-ready (hey, when I got it I had no intentions of ever doing anything more than droning away like most users, but then Ubuntu found me).  

I would assume that it's powerful enough, but I don't have 3D rendering, and I have tried to set up the drivers before, only to have to re-install Ubuntu and try again (twice).  I would really like to get some eye-candy on here so that my Vista-using friends will shut up about their (P)OS.

I am just wondering if I am going for the wrong drivers or what?  I am running 6.06LTS 32-bit version.  I love it all, and want more!

---

### Post by IntoTheLight on 2007-02-08
```
lspci -X
PCI:0:0:0 RAM memory: nVidia Corporation C51 Host Bridge
PCI:0:0:1 RAM memory: nVidia Corporation C51 Memory Controller 0
PCI:0:0:2 RAM memory: nVidia Corporation C51 Memory Controller 1
PCI:0:0:3 RAM memory: nVidia Corporation C51 Memory Controller 5
PCI:0:0:4 RAM memory: nVidia Corporation C51 Memory Controller 4
PCI:0:0:5 RAM memory: nVidia Corporation C51 Host Bridge
PCI:0:0:6 RAM memory: nVidia Corporation C51 Memory Controller 3
PCI:0:0:7 RAM memory: nVidia Corporation C51 Memory Controller 2
PCI:0:3:0 PCI bridge: nVidia Corporation C51 PCI Express Bridge
PCI:0:4:0 PCI bridge: nVidia Corporation C51 PCI Express Bridge
PCI:0:5:0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge
PCI:0:9:0 RAM memory: nVidia Corporation MCP51 Host Bridge
PCI:0:10:0 ISA bridge: nVidia Corporation MCP51 LPC Bridge
PCI:0:10:1 SMBus: nVidia Corporation MCP51 SMBus
PCI:0:10:2 RAM memory: nVidia Corporation MCP51 Memory Controller 0
PCI:0:11:0 USB Controller: nVidia Corporation MCP51 USB Controller
PCI:0:11:1 USB Controller: nVidia Corporation MCP51 USB Controller
PCI:0:13:0 IDE interface: nVidia Corporation MCP51 IDE
PCI:0:14:0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller
PCI:0:16:0 PCI bridge: nVidia Corporation MCP51 PCI Bridge
PCI:0:16:2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Cont roller
PCI:0:20:0 Bridge: nVidia Corporation MCP51 Ethernet Controller
PCI:0:24:0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyper Transport Technology Configuration
PCI:0:24:1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Addre ss Map
PCI:0:24:2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
PCI:0:24:3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Misce llaneous Control
PCI:3:6:0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Cont roller (PHY/Link)
PCI:3:8:0 Communication controller: Conexant HSF 56k Data/Fax Modem

```

I know what this info is, but I can't decipher it.  Does it even help?

---

### Post by IntoTheLight on 2007-02-08
```
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2) (prog-if 00 [VGA])
        Subsystem: Foxconn International, Inc.: Unknown device 0ca8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 50
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <available only to root>
```
Or how about this?

---

