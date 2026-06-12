---
title: "Cannot Get 1280x1024 Resolution, Why?"
date: 2005-10-27
forum: Multimedia &amp; Video
---

### Post by Breezy Badger on 2005-10-27
here is my code, I thought I had everything set right but I guess I am wrong  

it will not give me the option for 1280x1024 in the screen resolutions.

I think it may have to do with vert and horz syncs, anyone know?

I am guessing someone can pick this out easy, but to me I have just gone over it too much I guess

```
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
#       Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
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
        Identifier      "NVIDIA 5950 Ultra"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
        Option          "HWCursor" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       31-60
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA 5950 Ultra"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
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

```

Thanks,

Badger

---

### Post by aysiu on 2005-10-27
Everything you need to know:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by Xian on 2005-10-27
Check your available resolutions:

```
$ xrandr
```

You can test it on the fly (temp only):

```
$ xrandr --size 1280x1024
```

---

### Post by Breezy Badger on 2005-10-27
thanks for the helpful link, let me read there and see what I can find

---

### Post by Breezy Badger on 2005-10-27
ok I found out what the issure was, It was the sync rates, I had to go get the manual for my monitor and it worked great after restart.

thanks for the help guys

Badger

---

