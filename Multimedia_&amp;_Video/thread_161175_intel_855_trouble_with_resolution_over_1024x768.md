---
title: "intel 855 trouble with resolution over 1024x768"
date: 2006-04-16
forum: Multimedia &amp; Video
---

### Post by HadroLepton on 2006-04-16
i have an intel 855gme board with the intel integrated graphic. monitor is ibm thinkvision l200p, connected by dvi cable. both should be able to display 1600x1200 with 24bit color depth and 60hz. ubuntu recognized both devices correctly, at least by name, in xorg.conf.

my problem is that when i set the resolution to 1600x1200 the image will be squeezed to the left part of the monitor and the rest of the monitor is black. same happens when i set the resolution to 1280x1024, but this time with an additional black frame around the the left part, the monitor menu says it is set at 1600x1200.

when i connect the monitor using analog cable the image at 1600x1200 is shown correctly (but blurry). the 1280x1024 is also shown correct, but the image has a blackframe around, the monitor menu says it is set at 1600x1200.

every resolution 1024x768 and below works fine.

i have read many forum entries and wikipages about the intel 855 and 915 and the i810 driver from x.org. but all solutions posted doesn't seem to apply to my problem.

the output from some tools

```

$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)852GM/852GME/855GM/855GME Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)852GM/852GME/855GM/855GME Graphics Controller Hardware Version 0.0
memory: 32576kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 1 3
id: 4160
eisa: IBM4160
serial: 01010101
manufacture: 33 2003
input: analog signal.
screensize: 41 31
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
ctiming: 640x480@60
ctiming: 640x480@85
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1280x1024@60
ctiming: 1280x1024@70
dtiming: 1600x1200@60
monitorname: IBM L200P
monitorrange: 31-75, 56-85
monitorserial: 66-A8702

```

```

$ sudo 855resolution -l
855resolution version 0.4, by Alain Poirier

Chipset: 855GM (id=0x35808086)
VBIOS type: 2
VBIOS Version: 3360

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

```

```

$ sudo xresprobe driver=i810
id: IBM L200P
res: 1280x1024 1024x768 800x600 720x400 640x480
freq: 31-75 56-85
disptype: crt

```

and my xorg.conf

```

$ cat /etc/X11/xorg.conf
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
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

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "IBM L200P"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "IBM L200P"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

note that i added the 1600x1200 to the modes line in the display subsection. they were not there originally.

note2 i have also tried adding horizontal and vertical refresh values to the monitor section. that didn't change anything.

the xorg log file is quite long. i don't know which part of it will be usefull. a quick glance over it showed no errors. but maybe i just don't know where/how to look. if you need it i will post it.

thank you for reading this far :) please help.

---

### Post by HadroLepton on 2006-04-17
update:
i studied my xorg log file and found some interesting lines. i cannot paste lines directly because the machine in question is currently not connected to my network. but i will try to explain using lines from other xorg log files found in google

most apparent problem seems to be the ddc clock which is maxed at 130mhz. i get these warning lines for the 1280x1024 and the 1600x1200 resolutions.
[http://www.google.com/search?q=l200p+exceeds+ddc+maximum](http://www.google.com/search?q=l200p+exceeds+ddc+maximum)
as you can see there the max is sometimes 130 and another 170 yet another 200 mhz. the specs from my monitor manual says "clock frequency" is 130mhz when digital and 205 when analog.

i tried to disable ddc probing using an i810 driver option in the xorg.conf. that caused the warning lines in the log to disappear, but no difference in the squeezed image.

i do not understand why the same monitor seem to have different ddc maximums. there are two l200p models from ibm, both have 130mhz in the manual.

another case which got my attention is that my xorg log seem to be missing some information which other people get.
[http://wiki.x.org/wiki/FAQVideoModes](http://wiki.x.org/wiki/FAQVideoModes)
there is explained how one can assemble a mode line using the information from the log file.
these two lines are the important ones
```

 (II) I810(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
 (II) I810(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0

```
but my xorg log file do not have those lines. it could be that this information is no longer needed because i read somewhere else that xorg can now calculate the mode lines automatically so people no longer need to write their own modelines in xorg.conf.

any suggestions?

---

### Post by HadroLepton on 2006-04-24
i have now tested a different monitor and a different dvi cable. the other monitor said something along the lines of signal out of range, while the other dvi cable with my monitor gave the same squeezed image in the left part.

i have also tested installing windows xp, which didn't recognized the graphic card (in fact it didn't recognize much else either). i installed the intel graphic drivers from the supplied cd. after the mandatory reboot i got a black screen (monitor went to standby mode). booting in safe mode (vga mode) gives me resolutions up to 1024x768 which work fine, but anything higher will result in a black screen (standby).

i also tried ubuntu 6.06 beta live cd. same results (as ubuntu 5.10)

i don't understand how others seem to get ridiculous resolutions like 1337x101 to work. but i can't even get a standard resolution to work. *breaking out in tears*

---

