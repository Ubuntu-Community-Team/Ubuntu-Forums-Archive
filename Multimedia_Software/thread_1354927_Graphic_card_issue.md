---
title: "Graphic card issue"
date: 2009-12-14
forum: Multimedia Software
---

### Post by j3rryf4n on 2009-12-14
Hello,
First of all I'm new to Ubuntu.

Well,
I'm having an issue with my graphic card. I don't really know what's the real type of my graphic card. It has an ASUS cooler and it's motherboard is also ASUS. There is also ASUS written on the card's CD. I used Windows before, everytime I installed my graphic card then it installed 2 drivers. An ATi (catalyst center) and an ASUS, that was working fine.

I switched to Linux (Ubuntu 9.10 Karmic Koal) and now I don't have any idea how to get the REAL driver for my graphic card.

My card uses the name ASUS Extreme X550 ATi Series.

I can find the ATi driver, but it's named as ATi Radeon X550 Series. I tried out that driver on Ubuntu 9.04 Jaunty. When installed it and rebooted my PC then the screen frozen at the start-up image and was no sound and nothing happened. Couldn't even reset it. So I'm a bit scared to install that driver again.

I also found my graphic card on the ASUS' Global site, it's named as Radeon X550 (EAX550HM512/TD/256M), but there's not exist Linux driver; or is there?

Please, help me.

---

### Post by j3rryf4n on 2009-12-14
I'm currently using the default driver which got installed for first with Ubuntu 9.10.

---

### Post by Tricity on 2009-12-14
> **j3rryf4n said:**
> 
I also found my graphic card on the ASUS' Global site, it's named as Radeon X550 (EAX550HM512/TD/256M), but there's not exist Linux driver; or is there?


OK, so you know what card it is. BTW, the shell command 

lspci -v 

gives you a ton of information, such as:

00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        (...)

As you can see, I have an nVidia 61xx card, you seem to have the ATI Radeon X550. You should have a file /etc/X11/xorg.conf where your graphics card is defined. Open this file (as root) and look for a section the appears similar to :

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
EndSection

In the "Driver" line, there may other drivers, of course. Here are three that you could choose:

vesa - most conservative, should run with almost all cards, but is slow and may not use all capabilities.

radeon - Open source Radeon driver - should work

fglrx - Radeon's proprietary driver - uses all features, but I have experienced some instabilities in some systems

Try them.

---

### Post by Melcar on 2009-12-14
Ubuntu will load the open source driver on its own.  No need to mess with it unless you're experiencing problems.  The proprietary ATI driver( the one you would get from AMD's website, called fglrx) does not work for that particular chip anymore; the last version to offer support was 9.3 if I remember correctly, which does not work on the new Ubuntu release (8.10 I think was the last one).
You should have 2D and 3D acceleration as it is (although only OpenGL1.5, so don't try to run WINE or anything like that). Type: 

```
glxinfo | grep "renderer string"
```

...in a terminal and if the driver is working properly you should get a response similar to:

```
OpenGL renderer string: Mesa DRI R600 (RV770 9442) 20090101  TCL
```

---

### Post by j3rryf4n on 2009-12-15
> **Tricity said:**
> OK, so you know what card it is. BTW, the shell command 

lspci -v 

gives you a ton of information, such as:

00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        (...)

As you can see, I have an nVidia 61xx card, you seem to have the ATI Radeon X550. You should have a file /etc/X11/xorg.conf where your graphics card is defined. Open this file (as root) and look for a section the appears similar to :

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
EndSection

In the "Driver" line, there may other drivers, of course. Here are three that you could choose:

vesa - most conservative, should run with almost all cards, but is slow and may not use all capabilities.

radeon - Open source Radeon driver - should work

fglrx - Radeon's proprietary driver - uses all features, but I have experienced some instabilities in some systems

Try them.
When I typed lspci -v, then it said this:
04:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
    Subsystem: ASUSTeK Computer Inc. Device 0154
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=256]
    Memory at febe0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon, radeonfb

I think it's ok, or no? Why does it say 'Silent'?

---

### Post by j3rryf4n on 2009-12-15
> **Melcar said:**
> Ubuntu will load the open source driver on its own.  No need to mess with it unless you're experiencing problems.  The proprietary ATI driver( the one you would get from AMD's website, called fglrx) does not work for that particular chip anymore; the last version to offer support was 9.3 if I remember correctly, which does not work on the new Ubuntu release (8.10 I think was the last one).
You should have 2D and 3D acceleration as it is (although only OpenGL1.5, so don't try to run WINE or anything like that). Type: 

```
glxinfo | grep "renderer string"
```...in a terminal and if the driver is working properly you should get a response similar to:

```
OpenGL renderer string: Mesa DRI R600 (RV770 9442) 20090101  TCL
```
I got this: 
OpenGL renderer string: Mesa DRI R300 (RV380 5B63) 20090101 x86/MMX/SSE2 TCL

---

### Post by j3rryf4n on 2009-12-15
So umm... Does it mean everything is fine?

---

