---
title: "S Video to Component crashes after Boot?"
date: 2010-12-31
forum: Multimedia Software
---

### Post by insidiousraven on 2010-12-31
System:
[LIST]
[*]AMD Athlon II X2 240 Regor 2.8GHz 2 x 1MB L2 Cache Socket AM3 65W Dual-Core Processor ADX240OCGQBOX
[*]GIGABYTE GA-MA785GM-US2H AM3/AM2+/AM2 AMD 785G HDMI Micro ATX AMD Motherboard
[*]Patriot PSD22G8002 2GB PC2-6400 800MHz CL5 RAM
[*]EVGA 01G-P3-N959TR GeForce 9500 GT 1GB DDR2 PCI-Express 2.0
[*]300 watt power supply
[*]Barracuda 32MB cache 7200 RPM 1TB SATA hard drive (two of these)
[*] Ubuntu 32-bit 10.10
[/LIST]

Problem:
Ubuntu is installed and loads fine using the Video Card monitor port. When I try to use the 7 pin S Video port on the 9500 with the 7 pin S Video to Component cable that came with the Video card to display Ubuntu on my Toshiba TheaterView SD TV, it makes it through the boot/BIOS screen, and then crashes when trying to load Ubuntu.

Is there anyone who has experienced this, or who has any advice?  I have installed the NVIDIA accelerated graphics driver, and set the initial display setting in BIOS to PCI. 

What else can I do? My TV only has 4pin S Video, Composite and Component.  No HDMI :(

Edit: I've also tried using a 4 pin S Video cord to connect the video card to the TV, and for some reason that doesn't work either.

---

### Post by BicyclerBoy on 2010-12-31
When you say crashes.. do you really mean X server fails to start ?
If yes then you can still login & edit files (terminal text mode).

It is harder to fix the xorg.conf settings with a non-EDID monitor & screwed up settings. 

Try leaving the computer monitor attached until you have the TV working as you would like.
Use the nvidia-settings utility to enable the component display & configure as separate X screen, save to xorg.conf.

The next step is to optimise the video modes your TV will support. Trial & error..

Last step could be disconnecting the computer monitor: this will most likely mess up the xorg.conf settings.

---

### Post by insidiousraven on 2010-12-31
Ok, I've used NVIDIA X SERVER to get it to display on my tv via twin view.  However, I would like this computer to simply boot up directly onto the tv, with no other monitor attached whatsoever.  I don't seem to see any tutorials that don't involve a second monitor.  How do I get it to just work with the tv?

My old NVIDIA card worked fine with svideo, but it won't fit in my new motherboard, or I'd be using it. 

Anyone have a tutorial?  I'm desperate.

---

### Post by BicyclerBoy on 2010-12-31
You did not answer my question..

You do not want to use twinview or xinerama..
Select as a separate X window (configure button in nvidia-settings).
Save to xorg.conf file & exit.

Normally the video card initialisation process (bios boot) detects connected monitors & can display the bios POST on a component connected device.

Why rush to disconnect the PC monitor ?

The nvidia-settings program should generate a xorg.conf file with some hints...

After disconnecting monitor (if you must), reboot & if X server fails to load then simply login..
I think you will need to edit the file from terminal login 

sudo nano /etc/X11/xorg.conf

Nvidia xorg driver has built-in SD & HD video modes that will most likely work okay with TV.

The Xorg website has a good document that defines the X11/R6 xorg.conf file..

The TV will not provide EDID over component so you may need entries:

    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"

in the Screen section..

Note (for much later) that the RGB colour space is different for TV to PC monitor.

---

### Post by insidiousraven on 2011-01-02
Thank you for your help. Setting it as a Separate X Window, shutting down the pc, then booting it back up with the S Video cable worked.  I was able to get it the right resolution, and compensate for overscan.  The boot up and shut down screens are very ugly, but so long as the desktop is fine, I'm ok with it.

I wanted to disconnect the monitor so badly because it belonged to another computer. Again, thanks.  Solved my problem!!

---

### Post by BicyclerBoy on 2011-01-02
Good for you..

Note that s-video can only achieve SD resolutions 576 or 480 lines.

---

