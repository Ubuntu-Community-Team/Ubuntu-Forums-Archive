---
title: "Nvidia twinview/xinerama games help needed"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by bobbymcsteels on 2006-10-09
Ok have got xinerama working nicely but...... I have installed a few games using cedega but when I run them they are opened across both screens.... which is a major pain, so how can I make things open up in just one screen.
Cheers

---

### Post by bobbymcsteels on 2006-10-10
can anyone help me out with this?

---

### Post by Ziox on 2006-10-10
if you can, choose a smaller resolution, and select windowed mode instead of full screen

---

### Post by bobbymcsteels on 2006-10-11
the only problem with that is some things are off screen at the bottom for example, was playing americas army, and the decision botton was at the very bottom off the screen so I couldnt select it. Also on the 2nd screen there is no sound where as if i use the main screen there is perfect sound.

---

### Post by Tim Sawyer on 2006-10-12
Hi,

You can force your setup to only use one monitor at certain resolutions.  I haven't done this in Ubuntu but I did do it in Gentoo.  Here's a portion of my gentoo xorg.conf file, which should give you some clues.

Section "Screen"
    Identifier  "Screen 1"
    Device      "MSI 5900"
    Monitor     "tft left"
    DefaultDepth 24
    Option	"Twinview"
    Option	"SecondMonitorHorizSync" "24-80"
    Option	"SecondMonitorVertRefresh" "55-75"
    Option	"MetaModes" "1280x1024,1280x1024;1152x864,NULL;1024x768,NULL;800x600,NULL;640x480,NULL"
    Option	"TwinViewOrientation" "RightOf"
    Option	"ConnectedMonitor" "DFP,DFP"
    Option	"SWcursor" "1"
    Option	"HWcursor" "0"

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

It's the MetaModes stuff - if the game is configured to run at 1024x768, then only one monitor will be on at that resolution, because the other one has NULL.  If you switch up to 1280x1024 then that will work on both.

Hope that helps!

Tim.

---

