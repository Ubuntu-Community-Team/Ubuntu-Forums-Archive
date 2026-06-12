---
title: "Need drivers that work with nVidia Geforce3 TI 200"
date: 2009-08-27
forum: Multimedia Software
---

### Post by bearsomg on 2009-08-27
I have an nVidia GeForce3 TI 200 graphics card, and I can't seem to find the correct nVidia drivers for it. I have a wide-screen monitor with a native resolution of 1360x768 and the best resolution I can get right now is 800x600. I plan on replacing my Windows XP with Ubuntu 9.04, so I'm trying to find out how to do these customizations before I install it. Could someone please explain to me how to install nVidia drivers that work with the GeForce3 TI 200 graphics card or provide a link?


Thanks in advance.


Edit:

I have already tried editing the xorg.conf file, using the Hardware Drivers program to enable the drivers, downloading the nvidia-glx-96 and all its requirements but to no avail. I am still stuck with 800x600 and below, I know I did a fresh install before on my computer and it worked fine... I didn't do anything different this time except my monitor broke and I got a new one. Right now I have a Sanyo DP19649.

---

### Post by bearsomg on 2009-08-28
Following my last question about getting the right driver for my graphics card, I think I found out why it worked before but not now. Now for some reason I have two graphics card in there (don't remember why, think I was testing the other one.) Is there a way to make sure ubuntu CAN NOT see it, so that it is in the slot, but not connected to ubuntu? I don't think there is a way in the bios to do so... 

By the way, I cannot open my computer. I got everything all nice and neat around my desk, and I don't want to mess it up. Plus, last time I removed it, my graphics got all messed up.

My monitor is connected to the nvidia, not the second broken one.:confused::confused::confused::confused::confused:

Edit:

I managed to us xrandr commands to add a 1024x768 resolution to the default display mode, but when I choose it in the display menu, it tells me it can't use it. Any ideas?

------------------------System Info-----------------------------------------
Dell Dimension 8200
 Nvidia GeForce3 TI 200 graphics card
broken one is a number nine or something like that...
Intel Pentinum 4 Processor
1.5 GB RAM

---

### Post by IcarusR on 2009-08-29
Have you installed the restricted drivers ??

---

### Post by overdrank on 2009-08-29
Threads merged.If you have installed the nvidia drivers then you may use the command with the alt, F2 keys and enter ```
gksu nvidia-settings
``` set the resolution and save to the xorg. Hope this helps.

---

### Post by bearsomg on 2009-08-29
Well, yes, I have tried installing the restricted drivers, but they didn't work either. still just gave me the 800x600 and 640x480. I did find out the problem though. My monitor technically isn't a monitor, it's a TV. I plugged in an old monitor and the default resolution was changed to 1024x768. I tried editing monitors.xml to the native resolution for 1024x768, but that didn't work either. I am done with the nvidia drivers. Now when I install the correct one for my card, it find resolutions not supported by my monitor. I run ```
sudo nvidia-xconfig
```
and when I restart my screen is completely black because it goes to a resolution not supported by my monitor. When I delete those mode entries from xorg.conf, a reboot gives me the graphics error and I have to uninstall nvidia drivers and reconfigure the graphics to get it working again.



So my real problem is ubuntu is not detecting my tv as a monitor, and decides to use the default resolutions, 800x600 and 640x480. How can that be solved?

---

### Post by overdrank on 2009-08-29
> **bearsomg said:**
> I have an nVidia GeForce3 TI 200 graphics card, and I can't seem to find the correct nVidia drivers for it. I have a wide-screen monitor with a native resolution of 1360x768 and the best resolution I can get right now is 800x600.
Edit:
 Right now I have a Sanyo DP19649.

> **bearsomg said:**
>  Now for some reason I have two graphics card in there (don't remember why, think I was testing the other one.) Is there a way to make sure ubuntu CAN NOT see it, so that it is in the slot, but not connected to ubuntu? I don't think there is a way in the bios to do so... 

By the way, I cannot open my computer. I got everything all nice and neat around my desk, and I don't want to mess it up. Plus, last time I removed it, my graphics got all messed up.

My monitor is connected to the nvidia, not the second broken one.:confused::confused::confused::confused::confused:

Edit:

I managed to us xrandr commands to add a 1024x768 resolution to the default display mode, but when I choose it in the display menu, it tells me it can't use it. Any ideas?

------------------------System Info-----------------------------------------
Dell Dimension 8200
 Nvidia GeForce3 TI 200 graphics card
broken one is a number nine or something like that...
Intel Pentinum 4 Processor
1.5 GB RAM

> **bearsomg said:**
> Well, yes, I have tried installing the restricted drivers, but they didn't work either. still just gave me the 800x600 and 640x480. I did find out the problem though. My monitor technically isn't a monitor, it's a TV. I plugged in an old monitor and the default resolution was changed to 1024x768. I tried editing monitors.xml to the native resolution for 1024x768, but that didn't work either. I am done with the nvidia drivers. Now when I install the correct one for my card, it find resolutions not supported by my monitor. I run ```
sudo nvidia-xconfig
```
and when I restart my screen is completely black because it goes to a resolution not supported by my monitor. When I delete those mode entries from xorg.conf, a reboot gives me the graphics error and I have to uninstall nvidia drivers and reconfigure the graphics to get it working again.



So my real problem is ubuntu is not detecting my tv as a monitor, and decides to use the default resolutions, 800x600 and 640x480. How can that be solved?

Hi and I am no expert but I am a little confused. :)
 But in short you are trying to get a higher resolution on a TV monitor with the GeForce3 TI 200. 
Nvidia has stopped support for the old nvidia cards but how are you connecting the system to the tv monitor. S-video? It maybe your monitor does not support that resolution or the graphics card can not support it via the connection. I believe the best solution would be the nvidia drivers and maybe editing the xorg. Good luck.

---

### Post by bearsomg on 2009-08-29
> **overdrank said:**
> Hi and I am no expert but I am a little confused. :)
 But in short you are trying to get a higher resolution on a TV monitor with the GeForce3 TI 200. 
Nvidia has stopped support for the old nvidia cards but how are you connecting the system to the tv monitor. S-video? It maybe your monitor does not support that resolution or the graphics card can not support it via the connection. I believe the best solution would be the nvidia drivers and maybe editing the xorg. Good luck.
Yes, but not S-Video. My TV has a VGA Input, and I connected the VGA input to the VGA output on my Geforce3 TI 200. I know it supports that resolution, because it worked fine on Windows. Also, in the manual it says the supported resolutions are 640x480 at 60,72,75 refresh rate; 720x400 at 70 refresh rate; 800x600 at 56,60,72,75 refresh rate; and 1024x768, 1280x768, 1280x720, and 1360x768 all at 60 refresh rate. I had the working before on another installation of Ubuntu 9.04, but with my old Dell monitor that broke recently. It will not detect my TV aas a monitor because, well, it isn't. I have tried to edit monitors.xml with 1024x768 instead of 800x600, restarted the x server, and it didn't show up in the display dialog. So then I edited it into the xorg.conf as a mode, but that still didn't work. If I edited a Virtual line into xorg.conf, it could do the resolution in virtual mode, but not as a regular mode. When I tried using xrandr to apply it, it gave me 

xrandr: Configure crtc 0 failed

Is there a way to fake the monitor detection in any way? Like I said before, I plugged in my old monitor, and it detected it fine, and used it's native resoluton which is 1024x768, but when I restarted with the tv plugged in it reverted back to 800x600.


PS My final plan is to be able to use 1360x768, but right now I just want 1024x768 to work.


I don't know if it is possible, but I thought if all the monitors are storedsomewhere in the system, I could add a setting for my monitor so that can be the default setting.

---

### Post by bearsomg on 2009-08-30
I kept looking up more online, and I found the answer at freebsd.org. I figured out that it wasn't using the correct resolution because it didn't exist as a mode yet. So in my xorg.conf file under the monitors section, I added the lines 

```
HorizSync       31.47 - 48.36
    VertRefresh     56.0 - 75.0
    Modeline    "1360x768"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
```which enabled the correct hsync and vertical refresh rates that my monitor supported, and created the 1360x768 mode. All of the lower modes under 1360x768 are enabled now, and all the modes I want show up in the Display settings dialog.

:guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by masoud77 on 2009-08-31
Hi bearsomg,

I faced a similar issue while I tried installing Ubuntu on my father's PC. He doesn't use a TV as an output though. He has got a Dell monitor and Nvidia graphics cards. The max resolution that I was able to get was 800x600 even though it gave higher resolutions in Windows (dual boot).

I had installed the restricted graphics drivers and enabled them as well. But no joy. I was wondering whether your solution would work for other resolutions like 1280x800 and 1280x1024. Or will I have to change the numbers. If yes, what would those be?

Thanks,
Masoud 
Ubuntu 8.04 LTS

---

### Post by bearsomg on 2009-09-01
> **masoud77 said:**
> Hi bearsomg,

I faced a similar issue while I tried installing Ubuntu on my father's PC. He doesn't use a TV as an output though. He has got a Dell monitor and Nvidia graphics cards. The max resolution that I was able to get was 800x600 even though it gave higher resolutions in Windows (dual boot).

I had installed the restricted graphics drivers and enabled them as well. But no joy. I was wondering whether your solution would work for other resolutions like 1280x800 and 1280x1024. Or will I have to change the numbers. If yes, what would those be?

Thanks,
Masoud 
Ubuntu 8.04 LTS


OK, first of all, get rid of the restricted drivers, nothing good comes out of them. In synaptic, search for nvidia, and the only things that come up that should be installed are

xserver-xorg-video-nv,  smartdimmer, jockey-gtk, jockey-common. After you have made sure those are the only things installed in the list that comes up when you search nvidia, restart the computer. When you log back in, run the command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then run the command 

```
sudo gedit /etc/X11/xorg.conf
```

When xorg.conf opens, it should look like this: 

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

Scroll down to the monitor section, and add the lines 

```
HorizSync       31.47 - 48.36
VertRefresh     56.0 - 75.0
```

replacing the numbers with the correct settings for the monitor (horizontal sync range, and vertical refresh rate range.) Then run the command 

```
gtf 1280 800 60
```

for 1280x800 at 60 refresh rate. Change these settings for whatever resolutions you want to do at the certain refresh rates. It should output something like

```
# 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
  Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
```

Highlight the 

```
Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
```

part, and paste it into a new line under the monitors section of xorg.conf. Then in that line, delete the "_60.00" part in the "1280x800_60.00" part, minus the quotes. So now your xorg.conf should look something like: 

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync       31.47 - 48.36
    VertRefresh     56.0 - 75.0
    Modeline "1280x800"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

Now scroll down to the screen section and add the lines

```
DefaultDepth    24
    SubSection "Display"
        Depth    24
        Modes     "1280x800" "800x600" "640x480"
    EndSubSection
```

That should allow you to use the 1280x800 resolution at 60 refresh rate in Ubuntu. If you want to add more resolutions, go back through this tutorial and change the numbers with what you want to use, then simply add "modeline_name_here" to the Modes line in the Subsection display that you added. Make sure to backup this file to your documents or something, in case you lose it. By the way, you cannot ever reconfigure xorg.conf or you will lose all the settings that you just entered.:)

---

### Post by masoud77 on 2009-10-17
Thanks a ton, bearsomg.

The How To was excellent.

You rock :guitar:

---

### Post by bearsomg on 2009-10-17
I did find out how to do this with the Restricted drivers too. You will need them if you want to play any games on the computer otherwise they will run slow as junk. Just do the same thing after installing the drivers! (And make sure that you are using the correct drivers for your model)

---

