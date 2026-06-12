---
title: "[SOLVED] Problems with Intel video and 1680x1050"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by apastuszak on 2007-09-05
I am trying hard to configure a desktop with a 915 chipset to display my new monitor at 1680x1050.

I just went out and bought an Envision G218a1 22" Widescreen monitor.  My PC has an Intel 900 series video card, that Intel claims will quite happily drive a resolution that high.

I uninstalled the i810 driver and installed the "intel" driver.  I now have the option to choose 1680x1050, as well as other widescreen resolutions.

If I choose 1440x900, the image changes and takes up the full screen of the display.  If I choose 1680x1050 (my ultimate goal), the resolution changes, but the screen is only about 2/3 full, with large black bands on the left and right side of the screen.

Using the monitor controls to stretch the screen doesn't seem to help, since their maximum setting are not enough to fill the whole display.

The monitor section of the my xorg.conf looks like this:

```
Section "Device"
        Identifier      "Intel 915"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Envistion G218a1"
        Option          "DPMS"
        HorizSync       30-80
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 915"
        Monitor         "Envistion G218a1"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1440x900" "1280x800" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1440x900" "1280x800" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1440x900" "1280x800" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1440x900" "1280x800" "1024x768" "8$        EndSubSection
EndSection
```

If anyone can provide help with this, I would greatly appreciate it.

Andy

---

### Post by apastuszak on 2007-09-17
Looks like I fxed the problem by myself.  Here's what I did:

I uninstalled the intel xorg server and reinstalled the i810 server.

Ran sudo dpkg-reconfigure xserver-xorg and entered all my monitor information.  I also entered my video memory as 256 MB.  Not sure if I needed to do this, but it was worth a try.

I then installed 915 resolution and changed one of my modes to 1680x1050 and then modified my xorg.conf with the following lines:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 915"
        Monitor         "Envistion G218a1"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1440x900" "1280x800" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1440x900" "1280x800" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1440x900" "1280x800" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1440x900" "1280x800" "1024x768" "8$        EndSubSection
       SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1440x900" "1280x800" "1024x768" "8$        EndSubSection
EndSection
```

I then hit CTRL+ALT+BACKSPACE to kill X and it came right up in 1680x1050.

Andy

---

### Post by kellemes on 2007-09-17
Thanks a lot for providing the answer to your question.. others will be helped.
Please mark your post as solved.

---

