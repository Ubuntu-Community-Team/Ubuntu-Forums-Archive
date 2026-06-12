---
title: "Sample xorg.conf for 1024x768 24bit with vesa driver"
date: 2009-09-19
forum: Multimedia Software
---

### Post by GameboyRMH on 2009-09-19
I've seen a lot of people (understandably) having trouble getting 1024x768 resolution with the vesa driver. Here's a custom config file I made that will force 1024x768 with 24bit color at ~60Hz. Even though there are multiple modelines, you won't be able to change resolution as long as you're using this configuration. Tested with Ubuntu 9.04 and Xubuntu 9.04.
[B]
WARNING: Although this configuration sets a "safe" refresh rate of ~60Hz, I cannot absolutely guarantee that your hardware won't be damaged. Use at your own risk.[/B]

That said I've had no problems with LCDs, CRT monitors or CRT TVs using this configuration.

Simply overwrite /etc/X11/xorg.conf with these contents and restart:

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync 42.0 - 52.0 
    VertRefresh 55.0 - 65.0 
    Modeline "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796
    Modeline "800x600" 38.21 800 832 976 1008 600 612 618 631
    Modeline "640x480" 24.11 640 672 760 792 480 490 495 50
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Subsection "Display"
        Depth       24
        Modes       "1024x768" "800x600" "640x480"
       EndSubsection
EndSection

```If you have any trouble, start in recovery mode and select xfix to go back to the default configuration.

---

### Post by jakj on 2010-08-30
I just wanted to mention that I tried this because of the crap with Intel drivers going on now in 10.04 Lucid, and it does -not- work.  "Ubuntu is running in low-graphics mode  The following error was encountered. You may need to update your configuration to solve this.  (EE) VESA(0): Driver can't support depth 24 (EE) Screen(s) found, but none have a usable configuration."  If I then change the depth from 24 to 16, it does boot, but it still gives me only the 640x480 mode, both in the Monitors control panel and in xrandr.  Pity...I was hoping to get a system going that was a usable resolution but didn't crash every few hours. If this were my main box instead of a side one for occasional use, I would have switched away from Ubuntu completely, a while ago.

---

### Post by pip010 on 2010-12-28
it didnt wotk for me neither! im trying to isntall xbuntu 10.10 on old pc with relatively new card nvidia fx5200 agp. which does showup with: lspci

however no lan card :) so no inet since the install also doesnt recognize my pci-wifi card :(

i tried creating myself the xconf but i guess it ignores it for some reason!!!

---

### Post by amsterdamharu on 2010-12-28
> no inet since the install also doesnt recognize my pci-wifi cardWhat wireless card is it?
You obviously have Internet on another computer so you can download stuff and use USB to copy it to the other system.

Could you post the output of:
```
sudo lshw -C network
```To execute the command you can press alt + F1, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in ```
 
``` tags.

---

### Post by L3v1stus on 2011-06-06
you just saved me!

Thx a lot!

---

### Post by johnh10000 on 2011-07-15
> **GameboyRMH said:**
> I've seen a lot of people (understandably) having trouble getting 1024x768 resolution with the vesa driver. Here's a custom config file I made that will force 1024x768 with 24bit color at ~60Hz. Even though there are multiple modelines, you won't be able to change resolution as long as you're using this configuration. Tested with Ubuntu 9.04 and Xubuntu 9.04.
[B]
<snip>
.

Wow! it has been years, since I had to edit xorg.conf by hand... This daft ati card I had lying around and your config has finally given me 1024x768 back.

Don't talk to me about Nvidia! 640x380 ONLY!

Cheers friend!!!

---

### Post by edrich on 2012-01-27
Many thanks, GameboyRMH. I installed Ubuntu 11.10 two days ago on my desktop PC and have  been unable to get past 640x480 on my nVidia card (which works perfectly  with the live CD). My Acer laptop runs fine with 11.10 and no *xorg.conf*  file, so I tried removing it but that made no difference. I also tried  changing the resolution and colour depth in StartUp-Manager (which is  probably necessary anyway). Eventually, with the help of your code at the top, I  found that the following works:

```

Section    "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
EndSection

Section    "Monitor"
    Identifier    "Configured Monitor"
    VendorName    "nVidia Corporation"
    ModelName    "NV18 [GeForce4 MX 4000]"
    Horizsync    30.0-60.0
    VertRefresh    50.0-70.0
    Modeline "1024x768_50.00"  51.89  1024 1064 1168 1312  768 769 772 791  -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Option        "AddARGBGLXVisuals"    "True"
    DefaultDepth    24
    SubSection    "Display"
        Depth    24
        Modes    "1024x768"
    EndSubSection
EndSection

```The trick seems to be linking the identifiers between Device, Monitor and Screen. Hope this helps someone else.

Thanks again.

---

