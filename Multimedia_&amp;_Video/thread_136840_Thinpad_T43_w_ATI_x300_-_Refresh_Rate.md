---
title: "Thinpad T43 w/ ATI x300 - Refresh Rate"
date: 2006-02-26
forum: Multimedia &amp; Video
---

### Post by vrode on 2006-02-26
Is anyone using ATI x300 on their laptop w/ a different refresh rate than 50 Hz?

I even tried using latest ATI driver off ATI website w/ no changes to the refresh rate.

The problem is the default screen resolution of 1400 x 1050 is hurting my eyes (tiny fonts) and moving to anything lower make the fonts jagged and foggy.

This for my thinkpad t43 running ubuntu 5.10. I even tried Dapper with same results.

Any pointers will be appreciated.

Here's a cut and paste of my xorg.conf file:

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


Section "Device"
        Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       30-97
        VertRefresh     50-160
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection



regards,
/virendra

---

### Post by torx on 2006-02-27
You shouldn't change the resolution as that is your native resolution. In other words, your LCD screen will display crappily at any other resolution. Instead, change your DPI to a higher value.

> 
Section "Device"
Identifier "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
Driver "ati"
[COLOR="DarkOrange"]Option "DPI" "125 x 125"	# Change the 125 x 125 to a value which suits your screen.
Option "UseEdidDpi" "FALSE"[/COLOR]
BusID "PCI:1:0:0"
EndSection


ctrl-alt-backspace.

---

### Post by vrode on 2006-02-28
Just curious, are you using Thinkpad T43 w/ ATI x300? If so, what's your DPI set to? Better yet, can you share your xorg.conf file?


please advice.


regards,
/virendra

---

### Post by zojas on 2006-03-05
I measured the screen with a ruler, then told X how big the screen was. add this line to the Monitor section of /etc/X11/xorg.conf:

```

DisplaySize     305     230 # 1400x1050 116x116 dpi 1400/(mm/25.4)

```

I like small fonts, so I typically use 9 point bitstream vera fonts. you may want larger. but now at least X will understand how big your screen is. you will then probably want to go and turn up font sizes in varous control panels to suit your taste.

---

### Post by zojas on 2006-03-05
oh ya, and I am using a thinkpad t43. if I get time later maybe I'll post my whole xorg.conf for you. do you ever have any trouble with the laptop waking up? about 1 time in 10 it won't wake up for me.

---

### Post by vrode on 2006-03-05
that will be great and no I haven't had any issues w/ laptop waking up.


regards,
/virendra

---

