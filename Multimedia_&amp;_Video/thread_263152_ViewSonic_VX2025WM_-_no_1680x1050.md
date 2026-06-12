---
title: "ViewSonic VX2025WM - no 1680x1050"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by halon314 on 2006-09-22
I have a Gateway 508GE desktop PC.  I am an avid Ubuntu user and love it.  However, I recently upgraded my monitor to a ViewSonic VX2025WM, and since doing so, I can't get my screen resolution above 1280x1024.  Nor do I have any resolution options in the wider aspect ratio needed for this widescreen monitor.  I'm currently running 1280x1024 but since this is a widescreen monitor, everything looks stretched!

Please help!

that section of my my /etc/X11/xorg.conf looks like this:

---------------------------
Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "VX2025wm"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
        Monitor         "VX2025wm"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
---------------------------

I'd really like to see that 1680x1050 option in Gnome's 'screen resolution' preferences...

Any input would be appreciated.

---

### Post by htmlguy716 on 2006-10-09
The VX2025 only runs 1680x1050 at 60Hz. Replacing "1680x1050" with "1680x1050_60" should do the trick. If you need any more help, [see my howto](http://ubuntuforums.org/showthread.php?p=1597740) on the subject

---

