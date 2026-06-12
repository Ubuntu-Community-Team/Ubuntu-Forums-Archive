---
title: "horizontal line through picture"
date: 2008-06-21
forum: Mythbuntu
---

### Post by nrune on 2008-06-21
Okay this is weird. We upgraded to a 720p hd television. The graphics are great and looks good, except for where the screen pan's or zooms or changes or rappidly changes screen shots. There is this long z all across the screen. I have changed multiple setting on the Nvidia card and I am still clueless. Little help? 

lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:1b.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 50)
00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller
00:1e.0 ISA bridge: ALi Corporation PCI to LPC Controller (rev 31)
00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:1f.1 RAID bus controller: ALi Corporation ULi 5287 SATA (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)
02:11.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```

Asus motherboard, amd 64 cpu, pvr150, 1gb ram, GeForce 6200 LE

thanks in advance

---

### Post by matrex on 2008-06-21
I am having the same thing so if there is anybody out there pleaz answer

---

### Post by nrune on 2008-06-22
I reduced the resolution on the tv and it has reduced the appearance of the lines quite a bit, but it is still happening. 

The major problem I have now is the overscan and chopping of the image. on the top and bottom of the screen. 

Mike

uh.. nevermind the line is just as annoying as ever

---

### Post by nrune on 2008-06-24
Well some additional info see if I can get some help figuring this out. I have isolated the problem to playback only.  Playback profile I have curently is on high quality which does pretty good a controling the line split screen.  em

It occurs to me that I may not have described the problem sufficently. 

When the line occurs it looks like that the top half of the screen is ten frames ahead and the bottom half of the screen is ten screens behind. so if this is a straight line, on the screen it looks like this...
...|
..|

Ignore the "..." 

Any help?

Mike

---

