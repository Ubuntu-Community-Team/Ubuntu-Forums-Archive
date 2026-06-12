---
title: "quick question / quick answer? (video card)"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by hansderelict on 2007-12-05
i need to find out what type of video card my laptop has, since ubuntu is using a generic intel driver right now, and i know i need to change that. is there a good piece of diagnostic software or something else that i could use to find out? thanks.

---

### Post by kelbizzle on 2007-12-05
Type the command 

```
lspci
``` This will show you all the pci connected deviceds.

```
lspsci | grep vga
``` Will still print the devices but only show you the vga controller.

---

### Post by hansderelict on 2007-12-05
i changed the driver, and now it won't go into the proper resolution anymore.. any ideas what i can do?

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by kelbizzle on 2007-12-05
Back up your xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.120507
```

Then edit your config
```
gksudo gedit /etc/X11/xorg.conf
```

Focus on the screen section. Try adding the resolutions like this to your config. After which you need to logout and press CTRL+ALT+Backspace. 

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
Section "Extensions" 
        Option  "Composite" "enable"
EndSection


```

If this doesn't work for you issue this command to get your old config back
```
sudo cp /etc/X11/xorg.conf.120507 /etc/X11/xorg.conf
```

---

