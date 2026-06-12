---
title: "Xorg is Driving me nuts"
date: 2010-07-24
forum: Multimedia Software
---

### Post by prju68 on 2010-07-24
Since updating to Lucid, I have lost my xorg settings and cannot seem to get it back. My goal was to get the correct resolution on my main monitor and then enable the second.

I am running the Nvidia "current" driver. (195.36.24)

Main main monitor is a Samsung 171T with a native resolution of 1280x1024.
and the graphics card is a GeForce 8400 GS

But I cannot achieve this resolution. If I use Nvidia-settings it offers a best resolution of 1152x864.

The Xorg.log shows that it is seeing my attempt to set 1280x1024 and is abandoning it saying that it is not valid.

> 
(--) Jul 24 08:13:35 NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:5:0:0:
(--) Jul 24 08:13:35 NVIDIA(0):     CRT-0
(--) Jul 24 08:13:35 NVIDIA(0):     CRT-1
(--) Jul 24 08:13:35 NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) Jul 24 08:13:35 NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(II) Jul 24 08:13:35 NVIDIA(0): Mode Validation Overrides for CRT-0:
(II) Jul 24 08:13:35 NVIDIA(0):     NoEdidModes
(II) Jul 24 08:13:35 NVIDIA(0): Assigned Display Device: CRT-0
(WW) Jul 24 08:13:35 NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) Jul 24 08:13:35 NVIDIA(0): 
(WW) Jul 24 08:13:35 NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) Jul 24 08:13:35 NVIDIA(0):     "nvidia-auto-select".
(WW) Jul 24 08:13:35 NVIDIA(0): 
(II) Jul 24 08:13:35 NVIDIA(0): Validated modes:
(II) Jul 24 08:13:35 NVIDIA(0):     "nvidia-auto-select"
(II) Jul 24 08:13:35 NVIDIA(0): Virtual screen size determined to be 1024 x 768
(==) Jul 24 08:13:35 NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) Jul 24 08:13:35 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jul 24 08:13:35 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Jul 24 08:13:35 NVIDIA(0): Initialized GPU GART.
(II) Jul 24 08:13:35 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Jul 24 08:13:35 NVIDIA(0): Initialized OpenGL Acceleration


I have gone to as simple an xorg.conf file as I can and have tried editing this to get some results, but the results are always the same. 

I am guessing that the reason I am getting the no EDI message in the logs is because my monitors are all connected by VGA as I have a KVM switch in the way. So, one of my attempts was to attempt to turn off the EID checking with:

option "UseEDIDFreqs" "false"

no difference..

I have read more postings on this subject than any and am now lost. I'm feel like there are very few people out there who understand this and mostly people rely on good look and shots in the dark.
I happy to accept suggestions from any source!

My xorg.conf currently looks like this:

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 75.0
    Option         "DPMS"
    Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection


Thanks
Peter

---

### Post by robert shearer on 2010-07-24
> My goal was to get the correct resolution on my main monitor and then enable the second.


So plug the main monitor direct to the card ie. no kvm.
Then run...

```
sudo Xorg -configure
```

which will create an xorg file called Xorg.conf.new (in your home directory)

you can  edit it and then move it and rename it (as superuser) to /etc/X11/xorg.conf then reboot or restart the x-server.
(Replace the kvm)

**Do** back-up your current xorg.conf.

Now the xorg.conf should be run on boot rather than the xserver being set on the fly and defaulting to your kvm.

---

### Post by prju68 on 2010-07-24
Thank you! With our the KVM the correct resolution is determined automatically. So that certainly clears up that it is KVM switch that is getting in the way.  Xorg must now I guess be able to read the modes from the monitor. I thought however that the modeline would override this and allow we to set the resolution without it detecting the mode.

Peter

---

### Post by robert shearer on 2010-07-24
Since Karmic the X configuration is generated dynamically at boot.

This is good. 
Previously if you changed cards or monitor then the static xorg.conf would mean that X probably wouldn't start.

Getting newcomers to edit xorg.conf, well think of the first time you used the terminal.

Now cards and monitors are probed at boot without the need for an Xorg file and 95 % of the time things go well.

It is still being refined and one of the glitches seems to be kvm switches where the switch is 'seen' as it is before the monitor. (my old ps2 switch means that I get 600x800 @60 Hz for my CRT... ouch!)

So some of us need a static Xorg.conf. (we will have the usual problem if we change cards/monitors but can just delete the old xorg and let the system build a new one then modify it to suit)

As I understand it (and being a bear of very little brain in this area I may have it backwards :) ) there are plans to have a configuration file, in future releases, where snippets of  xorg could be included.

Then, the dynamic setting would occur for everyone and those of us with a kvm could have a snippet for the monitor only.
This would be read at boot and the dynamic setting adjusted to accommodate it.

In Lucid that file is present though inactive I believe. (well I can't get it to work ) at /usr/lib/X11/xorg.conf.d

There are other snippets there that do work such as configs for wacom tablets, synaptics touch-pads, mouses etc.

As to why the modelines don't work for you, how did you generate them ?

---

### Post by prju68 on 2010-07-24
Thanks Robert, that explains a lot. As for the mode lines I used gtf:


> gtf 1280 1024 75
  # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync


Which I picked up from one of the million how tos I read.

Peter

---

### Post by robert shearer on 2010-07-24
I know nothing about gtf.
Though the first google hits....

[http://linux.die.net/man/1/gtf](http://linux.die.net/man/1/gtf)
[http://gtf.sourceforge.net/](http://gtf.sourceforge.net/)

....indicate that it is a modeline generator for VESA settings and I do not think this applies, you use a supported graphics card and driver not the Vesa driver.

That may be rot but it is all I can think of. :)

 Wiser minds please chip in here if there is another explanation.

Cheers, Bob.

---

