---
title: "Soundblaster X-Fi Xtreme Audio: not working"
date: 2010-12-04
forum: Multimedia Software
---

### Post by rocketman768 on 2010-12-04
Just installed this card. Can't figure out what I need to do to get it to work. It's a pci express card. Here is the lspci -v.

```

04:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
        Flags: bus master, fast devsel, latency 0
        Bus: primary=04, secondary=05, subordinate=05, sec-latency=64
        Memory behind bridge: fe900000-fe9fffff
        Capabilities: <access denied>
        Kernel modules: shpchp

05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
        Subsystem: Creative Labs Device 0018
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at fe9fc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


```

Using Kubuntu here.

---

### Post by rocketman768 on 2010-12-12
Still not working. I have looked up every webpage I can on the issue, and I'm coming to the conclusion that it just won't work.

---

### Post by lidex on 2010-12-12
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by rocketman768 on 2010-12-13
Here's the alsa-info

[http://www.alsa-project.org/db/?f=6616987d31ecc5e4843745579bbd6a360a712a81](http://www.alsa-project.org/db/?f=6616987d31ecc5e4843745579bbd6a360a712a81)

---

### Post by lidex on 2010-12-14
Afraid I don't have any good news - could not find a solution.
Please sign on to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/622144](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/622144)

---

### Post by rocketman768 on 2010-12-17
So, it's been over a decade with me and Linux, and the issue is STILL sound card drivers. D4mmit.

---

