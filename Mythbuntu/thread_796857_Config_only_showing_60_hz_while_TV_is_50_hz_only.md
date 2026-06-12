---
title: "Config only showing 60 hz while TV is 50 hz only"
date: 2008-05-16
forum: Mythbuntu
---

### Post by trillex on 2008-05-16
Hello there, I'm pretty new to Ubuntu and MythTV so I'm unsure where to go from here and a visit to the IRC channel just made me almost forget about my little project - so as a last thing, I'd like to ask here. 

I've installed Mythbuntu on a Pundit BB barebone from ASUS with a P7131 Hybrid TV-card. The Pundit is plugged up to my rather oldish but trusty TV, a Hitachi 28" Widescreen (CL28WF - PAL). It's a big monster, but it's all I got. It's plugged into the on-board TV-out into a scart converter. 

It boots up fine and installation is a breeze. The problem is just that I cannot use my colorfix cable since it'll make the screen flicker, so I've gone through it black/white. I thought this was because the installation forced 60 hz on the television, while it can only do 50 hz. I just thought it was a matter of changing it in the configuration for it, but when I go in, I can only select 60 hz (Even though there is a wide selection of resolutions). I've tried with different models, which shows that they support 48-60 hz - but it will still only show 60 hz. I thought then, that it might be my graphicscard limiting it (Maybe it wasn't installed correctly) but it shows up properly in the configuration for it.

Anyone got any idea?

---

### Post by laga on 2008-05-17
What VGA card is that? Can you show us the output of ```
lspci
```?

---

### Post by trillex on 2008-05-17
It's SIS 650 or 651, which it is identified as. 

```

trillex@trillex-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated System [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] 

<4 other USB controllers>

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
```

I don't have it hook to the network yet, so I had to write it manually, hence why I cut it short.

---

### Post by trillex on 2008-05-17
Before I installed it was just connected to my television so I tried while it was plugged into my monitor as well as my television to see if it got further configuration on it - but it is pretty much the same. I can't even find a means to change the television's resolution and refresh rate or should I believe that it is just a clone of the monitor? 

What I also tried was to put TV output to PAL, PAL-D and PAL-DK (I'm from Denmark) but still suffer the same thing. The s-video cable needs a colorfix cable and if I don't put that on, it doesn't flicker, but is in black/white. With colorfix, it starts to flicker, but only on the mediacenter.

What's funny is that if I plug it in my stationary computer, it works without flickering.

---

### Post by laga on 2008-05-17
What kind of flickering is that? Slow vertical scrolling?

---

### Post by trillex on 2008-05-17
The picture is still for 1-3 seconds, but is in black and white. Then it goes into color and flickers downwards for a few seconds, then focuses again for 1-3 seconds without color once again.

---

### Post by trillex on 2008-05-18
I suppose it is either the television or the graphicscard so I'm just about to toss in the towel, as my wallet is empty. :/

---

### Post by trillex on 2008-05-19
Card has been confirmed not to work:

[http://www.mythtv.org/wiki/index.php/TV_Out#Known_NOT_Working](http://www.mythtv.org/wiki/index.php/TV_Out#Known_NOT_Working)

This topic can from now on be ignored.

---

### Post by trillex on 2008-05-24
Alright, I'm at a complete loss here. I bought a cheap PCI Geforce 5200 and put it in. It works fine and detects the television as a secondary screen, but it is still only running 60 hz and I am unable to change it.

---

