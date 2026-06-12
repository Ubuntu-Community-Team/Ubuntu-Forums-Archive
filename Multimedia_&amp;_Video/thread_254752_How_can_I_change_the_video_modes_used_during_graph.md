---
title: "How can I change the video modes used during graphical startup and text console?"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by jis on 2006-09-10
During graphical startup and during text console launched by Ctrl+Alt+F1, for instance, the screen is barrel distorted and my monitor (MAG DJ707) displays some text that advises to select certain video mode. The text is on top of everything else displayed on the screen, and I have to use the monitor button to get rid of it. How can I tell Xubuntu to use a more suitable video mode?

(BTW If you try Ctrl+Alt+F1 you can probably get back to GUI by Ctrl+Alt+F7)

---

### Post by Ziox on 2006-09-10
> **jis said:**
> During graphical startup and during text console launched by Ctrl+Alt+F1, for instance, the screen is barrel distorted and my monitor (MAG DJ707) displays some text that advises to select certain video mode. The text is on top of everything else displayed on the screen, and I have to use the monitor button to get rid of it. How can I tell Xubuntu to use a more suitable video mode?

(BTW If you try Ctrl+Alt+F1 you can probably get back to GUI by Ctrl+Alt+F7)

If you are using in console, then I don't think Xubuntu matters, because no Windows Manager/Graphic Manager is open....

---

### Post by jis on 2006-09-10
I have set this in xorg.conf:

```

Section "Monitor"
	Identifier	"MAG DJ707"
	Option	"DPMS"
	HorizSync	30-70
	VertRefresh	50-120
EndSection

```

I used the autodetected values that are also given by [Monitorworld.com]("http://www.monitorworld.com/Monitors/mag/dj707.html").

On the other hand, I don't know, if xorg.conf is applied in this context.

---

### Post by Ziox on 2006-09-10
> **jis said:**
> I have set this in xorg.conf:

```

Section "Monitor"
	Identifier	"MAG DJ707"
	Option	"DPMS"
	HorizSync	30-70
	VertRefresh	50-120
EndSection

```

I used the autodetected values that are also given by [Monitorworld.com]("http://www.monitorworld.com/Monitors/mag/dj707.html").

On the other hand, I don't know, if xorg.conf is applied in this context.

I think you can see what the computer detects of your monitor by using this command:

sudo ddcprobe

---

### Post by jis on 2006-09-10
It gives "monitorrange: 30-70, 50-120" in the last row.

---

### Post by Ziox on 2006-09-10
I suppose that the right value then....

---

### Post by jobezone on 2006-09-10
> **jis said:**
> During graphical startup and during text console launched by Ctrl+Alt+F1, for instance, the screen is barrel distorted and my monitor (MAG DJ707) displays some text that advises to select certain video mode. The text is on top of everything else displayed on the screen, and I have to use the monitor button to get rid of it. How can I tell Xubuntu to use a more suitable video mode?

(BTW If you try Ctrl+Alt+F1 you can probably get back to GUI by Ctrl+Alt+F7)

I once managed to change the resolution of the console by loading sisfb module, and after a restart, the console used a bigger resolution automatically. But I had a sis card, so the module was specific to it...

Try installing the program modconf (in Universe), then launch it, and browse all the modules. Maybe you'll find one called <yourgraphicdriver>fb. Load it, then restart.

---

### Post by jis on 2006-09-10
I have Matrox G400 or G450 (dual-head). How can I know which?
Is there way to uninstall modules, it they do not fit?

modconf gave these drivers for kernel/drivers/video/matrox:

>                &#9474;             g450_pll          - (No description available)                     &#9474;
               &#9474;             i2c-matroxfb      - (No description available)                     &#9474;
               &#9474;             matroxfb_accel    - Matrox unified accelerated driver              &#9474;
               &#9474;             matroxfb_base     - Matrox unified accelerated driver              &#9474;
               &#9474;             matroxfb_crtc2    - Matrox G400 second head support                &#9474;
               &#9474;             matroxfb_DAC1064  - Matrox unified accelerated driver              &#9474;
               &#9474;             matroxfb_g450     - (No description available)                     &#9474;
               &#9474;             matroxfb_maven    - Matrox G400 second head support                &#9474;
               &#9474;             matroxfb_misc     - Matrox unified accelerated driver              &#9474;
               &#9474;             matroxfb_Ti3026   - Matrox unified accelerated driver

Can anybody give a hint which one to load?

---

### Post by jobezone on 2006-09-10
> **jis said:**
> I have Matrox G400 or G450 (dual-head). How can I know which?
Don't you have some paper with the specs of your computer? I'm a bit rusty on how to find this, but try running lspci in the terminal.
> 
Is there way to uninstall modules, it they do not fit?

Yes, I like to use modconf, because it allows you to browse all the modules, and see which are loaded. If you press enter in one of the modules, it will load it, and in the future allways be loaded at startup (it essentially adds the module name to /etc/modules I think). If you want to take it out, you press enter on it again.
> 
modconf gave these drivers for kernel/drivers/video/matrox:
Can anybody give a hint which one to load?
In my experience, when I try loading drivers , they fail and aren't loaded if I don't have the hardware they are made for.
I would say that you may need one or a few of the fb ones. It sucks that they don't have a description. You could search for each module name on google, and see which one is for your specific videocard. I don't know a better way to find out, but others may.

---

### Post by jis on 2006-09-10
Unfortunately no papers. I think the card is G450 as "lspci -v" gives:
```
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. G400/G450 (rev 82) (prog-if 00 [VGA])
        Subsystem: Matrox Graphics, Inc. Millennium G450 32Mb SDRAM Dual Head
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at 42000000 (32-bit, prefetchable) [size=32M]
        Memory at 40800000 (32-bit, non-prefetchable) [size=16K]
        Memory at 40000000 (32-bit, non-prefetchable) [size=8M]
        Expansion ROM at 40820000 [disabled] [size=128K]
        Capabilities: <available only to root>
```


The screen seems to work rather well even if none of the drivers are loaded :) I think at least matroxfb_g450 is for the card.

---

### Post by jis on 2006-09-10
> **jobezone said:**
> 
In my experience, when I try loading drivers , they fail and aren't loaded if I don't have the hardware they are made for.
I would say that you may need one or a few of the fb ones. It sucks that they don't have a description. You could search for each module name on google, and see which one is for your specific videocard. I don't know a better way to find out, but others may.

I could install matroxfb_g450, but only after I ran modconf by sudo. When I loaded the driver, the modconf loaded automatically a couple of additional drivers that were in the list.

---

### Post by jis on 2006-09-10
I rebooted, but I see no change in the behavior during startup or text console. Probably it is more monitor related problem. (Distortion did not happen with other monitor.) I wonder, if the loaded drivers consume memory for nothing. I also wonder, which drivers were used before.

---

### Post by jis on 2006-09-10
I guess the default driver is told [here]("http://wiki.x.org/wiki/VideoDriverFAQ#head-3846aee67127e8e79c8ca61e521e70b34ee6d089").
Maybe the loaded driver is the one offered by Matrox?

---

### Post by jis on 2006-09-13
I can use both drivers to set a video mode that works well with the monitor. The problem is (still) that such a mode is not used during graphical startup (shutdown) and text console.

---

### Post by jis on 2006-09-13
> **jobezone said:**
> Try installing the program modconf (in Universe), then launch it, and browse all the modules. Maybe you'll find one called <yourgraphicdriver>fb. Load it, then restart.

Should I change xorg.conf somehow to use the new driver. The device section looks like this now:

```

Section "Device"
        Identifier      "0 Matrox Graphics, Inc. MGA G400 AGP"
        Driver          "mga"
        BusID           "PCI:1:0:0"
        Option          "OldDmaInit"            "True"
        Screen          0
        Option          "MonitorLayout"         "CRT, CRT"
EndSection

```

..so I should I change the Driver field?

---

### Post by Indras on 2006-09-15
Okay, everybody, hold up.  Changing your video driver or xorg.conf will have absolutely no effect on your text-mode (CLI - Command Line Interface).  Your kernel uses the vesafb (short for vesa framebuffer) device to set its resolution, which is the one that it uses for usplash as well as the CTRL+ALT+F1 through F6 consoles.

If you want to change the vesafb resolution, you have to modify grub to pass the vga parameter to your kernel before you even boot.  I wrote a decent tutorial on how to do this in another thread (though I'm thinking of making a more official HOWTO).  Here's a link:
[http://www.ubuntuforums.org/showthread.php?t=227513](http://www.ubuntuforums.org/showthread.php?t=227513)

---

### Post by jis on 2006-09-16
Thanks, Indras. It worked.

---

### Post by Indras on 2006-09-17
> **jis said:**
> Thanks, Indras. It worked.

You're welcome.  I also completed the HOWTO I was writing, you can find the full thing here: [http://www.ubuntuforums.org/showthread.php?t=258484](http://www.ubuntuforums.org/showthread.php?t=258484)

---

