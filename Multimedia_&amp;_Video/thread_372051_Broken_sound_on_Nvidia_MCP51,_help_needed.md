---
title: "Broken sound on Nvidia MCP51, help needed"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by Prometheum on 2007-02-27
Recently, though I do not know how, I managed to break my sound on Ubuntu. I have an HDA-Nvidia MCP51 card that had been functioning fine up until recently. The first time it broke, I was able to fix it with sudo modprobe snd-intel8x0, but now that won't work. I even upgraded to Feisty (as I had seen on the forums that Feisty handled this better) but even that didn't work. My laptop is fine except for this sound issue, I have everything else sorted out. I have attempted to compile and install the latest ALSA drivers, older ones that have been "known to fix the problem", and other stable ones, and none of them work. 
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lspci -vv
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

Can anyone please help me? I will post whatever other diagnostic/benchmark results are asked. If there is some way to reset my sound settings back to default (as I have booted off my Edgy and Feisty CD's and both have worked, so I know its not hardware, sound also works in WINE) then that would be great. Any help is appreciated.

---

### Post by Prometheum on 2007-02-27
To elaborate on a few things, sound works in Cedega, but when I try to play something in Rythmbox while running Cedega it say the interface is busy. Any help would be greatly appreciated.

---

### Post by rappiold on 2007-05-06
Has anyone helped you with this?  I have the same sound card and I can't get it to work
Can anyone please help.
I'm using dual boot with Vista and there I have great sound. 
Laptop HP dv2214us  AMD  Turion 64x2
Appreciate anyone's help.

---

### Post by TecnoVM64 on 2007-05-06
Try this solution:
[http://ubuntuforums.org/showthread.php?t=239995&page=5](http://ubuntuforums.org/showthread.php?t=239995&page=5)

(you'll need to install build-essential before you follow those steps)

---

