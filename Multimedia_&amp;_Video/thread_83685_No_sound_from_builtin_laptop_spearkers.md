---
title: "No sound from builtin laptop spearkers"
date: 2005-10-29
forum: Multimedia &amp; Video
---

### Post by traherom on 2005-10-29
Note: I'm not sure if this should go here or in the laptop category.

I've been using Hoary for several months now, and recently upgraded to Breezy. At no point during that time have I been able to hear sound out of the builtin speakers. However, the audio jack does work, and I can use headphones or external speakers. It's not bad, but it would be really nice to have the builtin speakers working.

Alsamixer shows pretty much everything turned all the way up, but there are a few things which refuse to go up at all. In the attached screenshot, I'm on the thing which I think is the problem. It's identified as "External amplifier," but I can't get it off 0.

Anyone know a way to fix the problem/force alsamixer to turn the volume up on that one?

Thanks in advance.

P.S. Extra info:

The machine an Emachines laptop. I don't remember the model number right now.

```
ryan@ramlap:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
**0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)**
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP
```

---

### Post by davidsrsb on 2005-10-29
I found that the built in speakers of my NEC laptop were treated as "pc speaker" and were muted by default on breezy

---

### Post by traherom on 2005-10-30
[QUOTE=davidsrsb]I found that the built in speakers of my NEC laptop were treated as "pc speaker" and were muted by default on breezy[/QUOTE]Maybe my speakers are just broken, (;)) but "PC speaker" is all the way up. That's the one that controls my headphone audio. I'm surprised that they aren't linked, but...

---

