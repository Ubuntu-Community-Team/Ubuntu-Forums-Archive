---
title: "Screen tearing after resolution change"
date: 2011-05-15
forum: Multimedia Software
---

### Post by Kschikan on 2011-05-15
After upgrading to 11.04, my screen resolution was reset to 1024x768. As the native resolution for my monitor is 1920x1080, I went to reset that. The resolution didn't exist in the Monitors applications, so I did the following:

```

kane@Griffin:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
kane@Griffin:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
kane@Griffin:~$ xrandr --addmode VGA-0 "1920x1080_60.00"
kane@Griffin:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1600x1200_50.00   49.9  
   1920x1080_60.00   60.0  
   1600x900_60.00   59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)

```

And then used the Monitor tool to change to the higher resolution.

The monitor adjust, but most of the screen shows tearing and doesn't update correctly. Hard to explain, so I attached a screenshot at 1024x768, working normally, and 1920x1080, fubar. I've cropped these images to get them to fit the forum limitations, but they still show the issue.

My monitor is an LG Flatron W2253TQ, my graphics card is an ATI Radeon HD 4650, although the manufacturer is Biostar. I'm using the default free drivers.

Any ideas?

---

### Post by Kschikan on 2011-05-22
More information: The title bar (which in natty has all the menu options, time, etc) updates just fine. Also, sometimes moving a window around causes redraws in the affected area but they seem to only redraw in black, not the window contents. 

I tried upping my virtual screen size but that didn't seem to help.

Including my xorg.conf if that helps anyone

```


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "Flatron"
    VendorName     "Biostar"
    ModelName      "LG W2253"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Default Device"
    Driver         "radeon"
    VendorName     "Biostar"
    BoardName      "M96 [Mobility Radeon HD 4650]"
    Option	   "BusType" "PCI"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Default Device"
    Monitor        "Flatron"
    DefaultDepth    24
    SubSection     "Display"
	Virtual   2048 2048
        Depth       24
    EndSubSection
EndSection


```

Any ideas on what I should try next?

---

### Post by Kschikan on 2011-05-29
Some updates:

I tried disabling modelines on startup (added radeon.modeline=0 to /boot/grub/menu.lst). Caused my login screen to not display, so I removed that.

I tried adding the following to my xorg.conf:

```

Section "Monitor"
        Identifier "HDMI-0"
        Option "Ignore" "True"
EndSection

Section "Monitor"
        Identifier "DVI-0"
        Option "Ignore" "True"
EndSection

```

on the advice of [http://en.gentoo-wiki.com/wiki/Nouveau#Phantom_and_unpopulated_output_connector_issues](http://en.gentoo-wiki.com/wiki/Nouveau#Phantom_and_unpopulated_output_connector_issues) (which I realize may be gentoo specific). No change.

Finally, I decided to try going back to the Gnome Desktop (aka "Ubuntu Classic"). IT WORKED! Screen resolution reset to 1920x1080 no problem. Possibly an error in Unity? I dunno.

---

