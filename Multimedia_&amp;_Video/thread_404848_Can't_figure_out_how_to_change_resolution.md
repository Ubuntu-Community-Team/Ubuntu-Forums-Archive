---
title: "Can't figure out how to change resolution"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by e^(i*pi) on 2007-04-08
I just purchased a new 19" widescreen monitor and i having some iussues with my screen resolution.  When I go to System->Preferences->Screen Resolution it says that my defualt is 640 x 480.  When I click on the dropdown menu there are no other options.   The manual that came with the monitor says that the optimum resolution is 1440 x 900 @ 60 Hz.  On my windows partition I can set it to a maximum of 1280 x 768, but have found that it looks best at 1280 x 720 @ 60 Hz.  My computer is a Dell Dimension 2300 and from what I can tell my video adapter is an Intel Extreme Graphics Controller 6.13.01.3162.  I am fairly new to all of this, so please excuse my elementary questions here.  Is the range of screen resolutions I have to choose from determined by my video adapter?  I understand that to use my monitor up to its optimum ability I may have to purchase a new video card.  Still though, why more choices on my windows partition that my linux?  And most importantly, what steps do I need to take to fix this.  Please let me know if anymore information is needed to help sort this out.  Also feel free to explain a little more about how all these things work, as I am very interested in knowing more than I do currently.  I'm working toward completely cutting the cord from windows, and I view these issues as challenges and learning experiences.  I will be grateful for any input.

---

### Post by Iowa Dave on 2007-04-09
I had a similar problem when I plugged a new LCD monitor into my Ubuntu box.  The instructions [_here_]("http://ubuntuforums.org/showthread.php?t=83973") helped me a lot.

Don't be put off by the amount of information. Print it out for ready reference then work your way through it.

Safety tip: be sure to back up any file before you change it. Write down the backup name so you can restore it later if you need to.

Good luck!

---

### Post by reclusivemonkey on 2007-04-09
> **e^(i*pi) said:**
> Is the range of screen resolutions I have to choose from determined by my video adapter?

Yes, that and your monitor of course. Is your graphics card onboard? If so you will most likely have to purchase a AGP/PCI graphics card to get 1440x900. My Nvidia FX5200 handles that just fine.

> **e^(i*pi) said:**
> Still though, why more choices on my windows partition that my linux?

Depends on how you have xorg setup. Personally, when I had an old CRT monitor, I could get 1152x864 on Linux but on 1024x768 on Windows.

> **e^(i*pi) said:**
> And most importantly, what steps do I need to take to fix this.  Please let me know if anymore information is needed to help sort this out.  Also feel free to explain a little more about how all these things work, as I am very interested in knowing more than I do currently.  I'm working toward completely cutting the cord from windows, and I view these issues as challenges and learning experiences.  I will be grateful for any input.

Read, read and read more. The internet is full of information on Linux and every aspect of it. I won't even give you a single starting link, as knowing how to find information is a more important learning process than the information itself. The first thing I would do if I were you would be to find some technical details on my graphics card and see what modes it does actually support.

When I upgraded from my old 17" CRT to a 19" widescreen, all I did was comment out my old refresh rates in xorg.conf, uncomment "DPMS" and add 1440x900 to my modes. No need for any modelines.

---

### Post by e^(i*pi) on 2007-04-10
So I used the "sudo dpkg-reconfigure xserver-xorg" command and added some resolutions and really really improved everything.  However, I was still not in a widescreen resolution (1024 x 768) so I decided to try again and see if I could get it even better.  On my next attempt however the monitor recognition failed and I got nothing but a black screen.  I rebooted and now the right most portion of the desktop is off the viewing screen.  It doesn't cut off much, just slightly more than the width of the shutdown button.  I tried the reconfigure command a couple more times with and still no auto-recognition.  It did auto-recognize the very first time I did this though.  Any ideas?

---

### Post by bur[n]er on 2007-04-19
I can't get my Dimension 2300 to go widescreen either, but if you are having the display off the sides, try just hitting the "auto" button on your monitor.

I've tried 915resolution and the i810-modesetting driver as well to no avail (both in apt, do a search).  These may work for you though.

For the record, I have an Intel Brookdale integrated video card.  I assume yours is the same.

---

### Post by reclusivemonkey on 2007-04-19
Post your xorg.conf.

To the OP: Sorry I missed your reply as well. Post your xorg.conf too and I will take a look.

---

### Post by bur[n]er on 2007-04-19
Currently displaying:  1280x1024

Monitor:  Acer AL1916W 19" widescreen capable of 1440x900 @ 60Hz (as verified in windows)
Onboard Video Card: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Xorg.conf:
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "AL1916W"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "AL1916W"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1440x1440" "1400x1050" "1280x1280" "1280x1024" "1280x960" "1152x921" "1152x864" "1024x768" "832x624" "800x600" "720x400" "64
0x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x1440" "1400x1050" "1280x1280" "1280x1024" "1280x960" "1152x921" "1152x864" "1024x768" "832x624" "800x600" "720x400" "64
0x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x1440" "1400x1050" "1280x1280" "1280x1024" "1280x960" "1152x921" "1152x864" "1024x768" "832x624" "800x600" "720x400" "64
0x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x1440" "1400x1050" "1280x1280" "1280x1024" "1280x960" "1152x921" "1152x864" "1024x768" "832x624" "800x600" "720x400" "64
0x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1280x768" "1280x1024" "1280x960" "1152x921" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x1440" "1400x1050" "1280x1280" "1280x1024" "1280x960" "1152x921" "1152x864" "1024x768" "832x624" "800x600" "720x400" "64
0x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by bur[n]er on 2007-05-09
For the record, I gave up to use a 4:3

---

