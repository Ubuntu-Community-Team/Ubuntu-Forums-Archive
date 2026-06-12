---
title: "Configure display through amplifier"
date: 2008-01-24
forum: Mythbuntu
---

### Post by ravennium on 2008-01-24
Hi,

I've been using kubuntu for a while and desided it's time to make a clean install with mythbuntu. (at this point some HW also changed...)

Setup is this:
Display: Samsung LE40M86
Amp: Yamaha rx-v861
Display card: GF 7600

I installed mythbuntu and selected the nvidia proprietary drivers.

If I connect the Display card to Samsung LCD with DVI -> HDMI the resolution is just fine. 1920x1080.

But when I try to add the yamaha to the chain, the resolution is only 1024x768. Now I tried to change it and managed to get 16.. x something..

**Is there any way to boot up with the samsung attached straight to my disp card, then save those settings and add the yamaha amp to the chain and boot with the correct resolution.**

Windows (R.I.P) tackled this fine. Also if I boot the machine having the TV connected straight to the card and then detach cords and add the amp to the chain, everything seems to work with higher resolution.

So basically linux did not recognize the amp correctly... Hope this was clear enough...

---

### Post by ravennium on 2008-01-24
Ok, a little more googling gave me this...

Some expert could comment is this possible?

I boot with the LCD connected straight to the display card.
I open up the xorg.cof and add:
       Option          "IgnoreEDID"
to the Monitor section.

Then I shutdown the system, attach the amplifier to the display chain and boot up again. Could this work :confused:
edit: or maybe just restart the X, no need to shutdown... even though linux boots up fast :D

---

### Post by tedder on 2008-01-24
Hey ravennium, I had trouble with this when sending my output through a Onkyo receiver with HDMI in and out. Here are the sections of my xorg.conf that I think were relevant for one reason or another.

General mythtv preferences- mainly, turning off the screensaver in most cases and keeping the lack of a mouse from hurting things.
```
Section "ServerFlags"
    Option         "Xinerama" "0"

    # 9/13/07 Added due to howto:
    # http://www.mythtv.org/docs/mythtv-HOWTO-22.html
    AllowMouseOpenFail # allows the server to start up even if the mouse doesn't work
    Option "blank time" "0"
    Option "standby time" "0"
    Option "suspend time" "0"
    Option "off time" "0"
    Option "NoPM" "1"
EndSection

```

Modelines, because I needed settings that were perfect for my Samsung monitor. The modelines are from the cmdline utility to generate them- I just can't remember the name of it.
```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid

    # Added 20070922, source: http://gentoo-wiki.com/HOWTO_Xorg_HDTV
    #Option          "IgnoreEDID"


    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 68.0
    VertRefresh     59.0 - 61.0
    ModeLine       "1800x980" 146.5 1800 1912 2104 2408 980 981 984 1014 -hsync +vsync
    Modeline "1800x1000"  149.54  1800 1912 2104 2408  1000 1001 1004 1035  -HSync +Vsync
    Modeline "1920x1020"  163.22  1920 2040 2248 2576  1020 1021 1024 1056  -HSync +Vsync
  Modeline "1920x1080"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

    ## Added 20070922, source: http://gentoo-wiki.com/HOWTO_nVidia_Drivers#Unable_to_validate_video_modes
    # Option "Metamodes" "1920x1080"

    # 9/13/07 Disabled due to howto:
    # http://www.mythtv.org/docs/mythtv-HOWTO-22.html
    #Option         "DPMS"
EndSection

```

Okay, this might be the best set of commands for you. They are the options that turn off size checks, EDID, etc. Again, these work for me- YMMV.
```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
    Option      "DPI" "100 x 100"

    # Added 20070922, source: https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/105957
    #Option "UseEDID" "False"
    #Option     "UseEDID" "False"
    Option      "ModeValidation" "NoDFPNativeResolutionCheck, NoMaxSizeCheck"
    Option      "NoLogo" "True"
    Option      "ConnectedMonitor" "DFP"
    Option      "TVStandard" "HD1080p"
EndSection

```

Finally, my screen size overrides. These were necessary to force my Nvidia card to use the size I really wanted.
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    #Option         "metamodes" "1800x980_60.00 +0+0; 1024x768 +0+0"
    #Option         "metamodes" "1920x1080"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080" "1800x1000" "1800x980" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        # The Samsung doesn't overscan if you turn on the 'just scan' setting, 1x1 pixel mapping.
        ##Virtual       1800 1000
        Virtual 1920 1080
    EndSubSection
EndSection

```

Let us know if that works. Use my settings as a buffet- pick and choose what works for you. I suspect the best will be the Device options, but you may also have to hardcode the display size like I did.

-ted

---

### Post by ravennium on 2008-01-28
Today I had opportunity to try thing out...
I took those settings (some) and tried it.

IT WORKS, Oh My, oh my :guitar:
BIIIG THANKS to you tedder!

And tedder, if you ever visit finland, I'll buy you a beer :D
And if you like, I can heat the sauna :D

But if your underaged, have popcorn :popcorn:

---

### Post by tedder on 2008-01-28
glad it worked!

drinks and sauna are quite nice for me :-)

---

