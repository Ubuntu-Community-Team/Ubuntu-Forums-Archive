---
title: "Tv-out only in open source ati driver?"
date: 2009-08-21
forum: Multimedia Software
---

### Post by maximouse on 2009-08-21
I have a mythtv box that's connected to a PAL tv via S-video. It has no other monitor. I was wondering if someone has any idea if it is possible to get this to work with the open-source driver.
I know about the:
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --rate 50
trick, but it only seems to work if there already is a monitor connected.
Any help would be appreciated.

---

### Post by themgt on 2009-08-21
It works on mine (Radeon X300) although I had to set the TV standard to NTSC to get a picture. I also had to turn off DRI otherwise Mythfrontend  displayed only blank rectangles.
I'll be installing a Geforce 7300 as soon as the postman turns up with it.

My current xorg.conf

```

Section "Monitor"
        Identifier      "TV-monitor"
        DisplaySize     272 153  # or 203 143 for 4:3
        Option          "PreferredMode" "800x600"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "800x600"
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "DRI" "off"
        Option          "ForceTVOut" "on"
        Option          "TVStandard" "ntsc"
        Option          "monitor-S-video" "TV-monitor"
EndSection

```

---

### Post by maximouse on 2009-08-22
Well, it's still not working properly, but that actually helped a lot since now it actually displays something on the screen, even if it's just garble. The card is a RV200.

---

### Post by themgt on 2009-08-22
That sounds like the picture I got when I set the output to PAL.

---

### Post by maximouse on 2009-08-23
I got it to work, even in PAL mode. Your xorg.conf actually worked, I had just forgotten to "--purge remove" the fglrx driver.

I will however as well find a nvidia card, because without dri it is quite slow.

Thank you for the help non the less.

---

