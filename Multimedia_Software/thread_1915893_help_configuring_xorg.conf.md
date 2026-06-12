---
title: "help configuring xorg.conf"
date: 2012-01-27
forum: Multimedia Software
---

### Post by sonicb00m on 2012-01-27
I have an LCD TV connected to my Ubuntu installation on the DVI port. Unfortunately, if the TV is not on when the computer boots up it doesn't show anything on the display unless I restart X server.

I was hoping I could edit xorg.conf to force the LCD TV settings and this would fix the problem.

Currently my xorg.conf reads as follows (using the ATI 11.12 driver on my Radeon 5450 card)

```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

I would like to fix the resolution at 1920x1080 but I am unsure what the refresh rate of the TV is at currently.

Is there any way I can find out what it is currently set to and then what do I need to put in xorg.conf to force the resolution and refresh rate?

Will this fix my problem with the black screen when starting up the computer without the TV on?

Thanks!

---

