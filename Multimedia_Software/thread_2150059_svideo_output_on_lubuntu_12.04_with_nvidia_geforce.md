---
title: "svideo output on lubuntu 12.04 with nvidia geforce 5200"
date: 2013-05-30
forum: Multimedia Software
---

### Post by Vontux on 2013-05-30
Hello, this is a question that I also just posted onto the askubuntu.com site, I don't know which gets more traffic, the forums or that so I chose to post on both, I'll be sure to distribute the answer across both. At any rate, here is my issue, and thanks in advance for any help it is greatly appreciated:

I have an old computer that until recently was sitting around gathering dust. I decided to convert it into an XBMC box, and things went well until I decided to move it from the monitor I was using to configure it to the TV I wished to watch it on. The computer has an nvidia geforce 5200 card with an svideo output port. I installed version 173.14.36 of the nvidia drivers but I'm afraid I don't see any way to switch to svideo output, xrandr does not seem to detect the svideo abilities of the card, but I have produced the following to verify that the system does seem to detect the svideo out:

```
nvidia-xconfig --query-gpu-info
Number of GPUs: 1

GPU #0: Name : GeForce FX 5200 PCI BusID : PCI:2:0:0

Number of Display Devices: 2

Display Device 0 (CRT-0): EDID Name : ACI ASUS VH192 Minimum HorizSync : 30.000 kHz Maximum HorizSync : 80.000 kHz Minimum VertRefresh : 55 Hz Maximum VertRefresh : 75 Hz Maximum PixelClock : 140.000 MHz Maximum Width : 1280 pixels Maximum Height : 1024 pixels Preferred Width : 1366 pixels Preferred Height : 768 pixels Preferred VertRefresh : 60 Hz Physical Width : 410 mm Physical Height : 230 mm

Display Device 1 (TV-0): No EDID information available.
```

Ask Ubuntu Thread: [http://askubuntu.com/q/302220/163215]("http://askubuntu.com/q/302220/163215")

---

### Post by Vontux on 2013-05-30
I don't know if this adds any useful information, but I just noticed that while booting, and shutting down the command line interface displays on the the tv attached via svideo just fine, but as soon as x starts the video signal is lost.

---

