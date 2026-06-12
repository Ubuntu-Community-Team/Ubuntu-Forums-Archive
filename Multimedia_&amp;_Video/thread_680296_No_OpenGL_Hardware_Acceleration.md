---
title: "No OpenGL Hardware Acceleration"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by elicoten on 2008-01-27
What reasons could there by why I can't get Hardware acceleration with OpenGL. How can I find out if my hardware even supports it? I would think it probably would support it but it doesn't seem to be working. My graphics card is neither NVidia nor ATI - I think it SiS, and there are no restricted drivers for it.

Thanks for any assistance

---

### Post by tommcd on 2008-01-27
First, find out what video card you are using. Type <sudo lspci -v> in terminal and look for a section like this:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GM
L Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0110

```

Google the name of your video device to find out if there what linux driver is available for it. Also check the driver section of your xorg.conf. Type <less /etc/X11/xorg.conf>  in terminal and scroll down to the driver section to see what driver you are using. I don't think you are going to get much hardware accleration with a Sis video card.

---

### Post by elicoten on 2008-01-28
```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 2430
        Flags: 66MHz, medium devsel, IRQ 5
        BIST result: 00
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0100000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 9000 [size=128]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] AGP version 2.0

```

```
Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
EndSection

```
How do I know if there's a better driver available? Is it that the card doesn't support hardware acceleration or is it that there are no compatible drivers that support it? Could another OS (Windows, for example) do hardware acceleration with this card?

Also would this explain why I can't get COMPIZ to work?

Thanks

---

### Post by tommcd on 2008-01-28
It seems you are using the right driver:
[http://www.angelfire.com/linux/t_johnson/](http://www.angelfire.com/linux/t_johnson/)
[http://tldp.org/HOWTO/Hardware-HOWTO/video.html](http://tldp.org/HOWTO/Hardware-HOWTO/video.html)
Scroll down to find the relevant info on both those links. Google is your friend for stuff like this:
[http://www.google.com/linux](http://www.google.com/linux)
I don't think that card will offer much in the way of 3D performance. I wouldn't know if windows would offer better performance.
EDIT: It seems Sis does offer linux drivers, but they are very old (2002).
[http://www.sis.com/download/download_step1.php](http://www.sis.com/download/download_step1.php)
I would stick with the driver Ubuntu is using. Those are Red Hat rpm drivers anyway.

---

### Post by elicoten on 2008-01-29
So is it correct that Direct Rendering should be ot available, and consequently Compiz won't work?

Thanks for your advice.

---

### Post by elicoten on 2008-01-29
When I run GLXGEARS I get 220-245 frames/sec at the size it starts up and if i maximise it, it drops to 20-30FPS. Are those figures normal/what I should expect? On [http://www.angelfire.com/linux/t_johnson/](http://www.angelfire.com/linux/t_johnson/) his GLXGears FPS are higher than mine and he seems to have a similar graphics card. Is he running GLXGears maximised or normal screen size? 

Is there anything that I should do to the laptop/configuration to improve these figures?

Thansk

---

### Post by tommcd on 2008-01-29
> **elicoten said:**
> When I run GLXGEARS I get 220-245 frames/sec at the size it starts up and if i maximise it, it drops to 20-30FPS. Are those figures normal/what I should expect? On [http://www.angelfire.com/linux/t_johnson/](http://www.angelfire.com/linux/t_johnson/) his GLXGears FPS are higher than mine and he seems to have a similar graphics card. Is he running GLXGears maximised or normal screen size? 

Is there anything that I should do to the laptop/configuration to improve these figures?

Thansk

It is normal for glxgears fps to decrease when the "gears" window is maximized. With my nvidia 6200 I get about 1600+ fps, but the fps go way down if I mazimize the window. I would think the guy on the angelfire site is probably running glxgears at the normal size.
I have never used compiz or beryl. I turn off composite in my xorg.conf. I always favor snappy performance over eye candy. Is the laptop running slow or something, or is it just that compiz runs poorly? You should expect some performance penalty with compiz running because of the extra demand on the video card, and likely the CPU also, especially with a low end video card.

---

