---
title: "Help Needed with Samsung Lcd HDTV"
date: 2009-09-06
forum: Multimedia Software
---

### Post by ultima on 2009-09-06
Hello, 

Really strange problem I'm having here, everything is huge on the screen like I have an incorrect resolution but as you can see from the attached screen shot it is says its running at the correct resolution.

The correct Resolution for this TV being 1920x1080 @ 60Hz with a pixel clock Freq of 148.5

I have tried a few things like putting a modeline in the xorg config but that does nothing.

And sad to say it does work with Vista :) 
After I change the Hz from 24Hz to 60Hz that is.

btw I'm using Asus/Nvidia EN9500GT Video Card and have the same problem with or without Nvidia driver 

Thanks

---

### Post by tgalati4 on 2009-09-06
Post the output of:

cat /etc/X11/xorg.conf

Check your previous versions as well.  Sounds like you have a virtual display set up:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 779
	EndSubSection
EndSection


Try commenting it out or deleting it.

The other possibility is that you are not using DVI but actually putting out an HDMI signal through the DVI port using the Windows driver.  I don't know how you would test for this though.  Perhaps look through the Samsung menu or look at the input list and see what input is active.

---

### Post by ultima on 2009-09-07
Thanks for the reply

cat /etc/X11/xorg.conf is

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

I played around with the xorg.conf a week or so ago but couldn't get it working so I'm just testing with the live cd at the moment. 

I'm using the HDMI/DVI port so I'm pretty sure the signal is  DVI because when you plug it into another port the font looks weird like the tv is using video filters.

---

### Post by ultima on 2009-09-08
Update:

Works fine with Ubuntu 8:10.

Does anyone know what's changed Since?

---

### Post by ultima on 2009-09-08
Solved

The problem is to do with DPI

I found out from the Xorg log that the dpi should be set to 96x96 dpi but when I looked in nvidia-settings it was set to 305x305.

So the solution was to put "Option "DPI" "96 x 96""
in the xorg.conf file.

**xorg.conf**

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       26.0 - 81.0
    VertRefresh     24.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    Option         "DPI" "96 x 96"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection




```

---

### Post by tgalati4 on 2009-09-09
Good catch.  I love it when people solve their own problems and share their solutions.

That is the beauty of open source.  Most things are fixable.

Of course you were aware that there was a major xorg change from 8.10 to 9.04.

---

### Post by ultima on 2009-09-09
> Of course you were aware that there was a major xorg change from 8.10 to 9.04.

I figured as much, I even tried the Fedora 11 Live cd and it had exactly the same problem. 

So I new the problem must be with Xorg.

---

