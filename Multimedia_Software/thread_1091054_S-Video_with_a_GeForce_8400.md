---
title: "S-Video with a GeForce 8400"
date: 2009-03-09
forum: Multimedia Software
---

### Post by paragonconcept on 2009-03-09
I'm trying to enable S-Video output so i can hookup my TV. I have the latest nVida 1.8 driver installed, but i can't seem to get it to detect an external tv. Any Ideas? I'll post my xorg.conf 

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
Option "Composite" "Enabled"
EndSection
```

---

### Post by warp99 on 2009-03-09
Nvidia uses a non-standard connector for TV-out, it's a connector with 3 RCA outputs and an S-Video adapter. You have to make sure you have this connector or TV-out will not work. 

Now you can just use a standard 4 pin S-Video cable, but you have to break off the little plastic guide pin in order for it to fit on the back of the video card. With this you'll only get video for x-server, no console mode. So your best bet is to have the special connector out for composite TV if you need console mode.

The only changes you need to make to your xorg.conf for TV is to add the following:

```

Section "Device"
        Option          "TVStandard" "NTSC-M"  <- or PAL
        Option          "MetaModes" "1024x768" <- or "800x600"
        Option          "UseDisplayDevice" "TV-0" <- TV only Display
        Option          "TVOutFormat" "COMPOSITE" <- or S-VIDEO
EndSection

``` 

If you want to run TV and a monitor or any other options information is available here:

[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.37/README/chapter-15.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.37/README/chapter-15.html)

I had an awful time getting my nvidia 6200 TV port to work. I basically got the port to work first with an S-Video cable, a composite adapter, and setting the TVOutFormat option in xorg.conf to "S-VIDEO". Once the picture was established I switched over to the composite output on the connector, got a fuzzy picture, changed the TVOutFormat to "COMPOSITE", and rebooted the computer. Only at that point did the composite TV output, and more important console mode, finally work.

---

### Post by paragonconcept on 2009-03-09
I was able to get the TV to show something by using the S-Video connector. 

I had been doing an S-Video to composite adapter. Switching to pure Svideo fixed it. 

However, now this only shows the bios, and ubuntu splash screen. once X kicks in, it goes black. 

When i goto nvidia-settings - it says the TV is disabled, and that i'd need to restart to give it its own X-Session. After X is restarted, the TV display option goes back to being disabled in nvidia settings.

Here is my new xorg.conf output:

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

    Option         "Xinerama" "1"
EndSection

Section "InputDevice"

    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "STN SAMTRON"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
 VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x1024_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "TV-0"
    Option         "metamodes" "TV: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enabled"
EndSection


---

### Post by warp99 on 2009-03-09
Your xorg.conf file is a "mess". Here's a cleaned up version that should work.

```
Section "ServerLayout"
	Identifier 	"Default Layout"
	Screen 0 	"Screen0" 
	Screen 1 	"Screen1" RightOf "Screen0"
	InputDevice 	"Generic KeyBoard" "CoreKeyboard"
	InputDevice 	"Mouse" "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbOptions"    "altwin:super_win"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
	Identifier 	"Mouse"
	Driver 		"mouse"
	Option 		"Protocol" "auto"
	Option 		"Device" "/dev/psaux"
	Option 		"Emulate3Buttons" "no"
	Option 		"ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier 	"Monitor0"
	VendorName 	"Unknown"
	ModelName 	"STN SAMTRON"
	HorizSync 	30.0 - 85.0
	VertRefresh 	50.0 - 160.0
EndSection

Section "Monitor"
	Identifier 	"Monitor1"
	VendorName 	"Unknown"
	ModelName 	"TV-0"
        HorizSync 	30-50
        VertRefresh 	60
EndSection

Section "Device"
	Identifier 	"Device0"
	Driver 		"nvidia"
	VendorName 	"NVIDIA Corporation"
	BoardName 	"GeForce 8400 GS"
	BusID 		"PCI:2:0:0"
	Option          "NoLogo" "True"
       Option          "TwinView"
        Screen          0
EndSection

Section "Device"
	Identifier 	"Device1"
	Driver 		"nvidia"
	VendorName 	"NVIDIA Corporation"
	BoardName 	"GeForce 8400 GS"
	BusID 		"PCI:2:0:0"
        Option          "NoLogo" "True"
        Option          "TVStandard" "NTSC-M"
        Option          "TVOutFormat" "COMPOSITE"
        Screen          1
EndSection

Section "Screen"
	Identifier 	"Screen0"
	Device 		"Device0"
	Monitor 	"Monitor0"
	Option 		"metamodes" "CRT: 1280x1024_60 +0+0"
	SubSection 	"Display"
		Depth 24
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"Screen1"
	Device 		"Device1"
	Monitor 	"Monitor1"
	Option 		"metamodes" "TV: 640x480 +0+0"
	SubSection 	"Display"
		Depth 24
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "AIGLX" "True"
        Option          "Xinerama" "False"
EndSection

Section "Extensions"
	Option 		"Composite" "Enabled"
EndSection 
```

---

### Post by warp99 on 2009-03-09
After reading your post again you may need to change the following:

```
Option "TVOutFormat" "COMPOSITE"
```
to
```
Option "TVOutFormat" "S-VIDEO"
```

---

### Post by paragonconcept on 2009-03-09
My TV can handle composite, and i have those cables from nVidia. Is there any benefit to using that over s-video? 

I'll give this a shot when i get home today.

Thanks

~Jack

---

### Post by bmj2728 on 2009-03-09
S-Video is limited in it's actual resolution. I've heard varying numbers but it can't exceed 1280 X 720. It depends on what you intend to do with the TV as to whether it is worthwhile. If it's for watching internet video and DVDs then you'll bt fine with the S-Video. I have a Geforce 9500 GT and use the "HD out" connection from the S-Video. I get a max resolution of 1024 X 768 in Ubuntu, but with huge overscan issues, that are still a work in progress.

---

### Post by warp99 on 2009-03-09
> **paragonconcept said:**
> My TV can handle composite, and i have those cables from nVidia. Is there any benefit to using that over s-video?

S-Video is suppose to have better picture quality then composite out because of the way the signal is output, but the difference is not that noticeable, well at least not for me. I would use the output that gives you console mode and x-server. In other words TV picture from boot to desktop.

The real limiting factor is the resolution of analog TV (480 lines of interlaced horizontal resolution). This is why the card is set to a max of 1024x768 for that port. Anything higher is not going to make any difference.

---

### Post by paragonconcept on 2009-03-09
So i swapped out my xorg.conf for the one you posted, and changed composite to s-video.

I still don't get a picture when xorg is active. 

I launched nvidia-settings to see if there was anything in there, and it's still set to disabled.

---

### Post by paragonconcept on 2009-03-10
I unplugged my Monitor and it worked.... 

Is there something i need to do so i can mirror them?

---

### Post by warp99 on 2009-03-10
Twinview enabled means having one x-server span across multiple monitors in various configurations:

[ftp://download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-13.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-13.html)

While the dual configuration you currently have is for an x-screen on each monitor:

[ftp://download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-15.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-15.html)

If you remove the twinview option from the "Device" section both monitors at that point should have an x screen. If you just want to mirror one monitor onto the other using twinview than use this xorg.conf instead:

```
Section "ServerLayout"
	Identifier 	"Default Layout"
	Screen 0        "Screen 0"
	Screen 1        "Screen 1"
	InputDevice 	"Generic KeyBoard" "CoreKeyboard"
	InputDevice 	"Mouse" "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbOptions"    "altwin:super_win"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
	Identifier 	"Mouse"
	Driver 		"mouse"
	Option 		"Protocol" "auto"
	Option 		"Device" "/dev/psaux"
	Option 		"Emulate3Buttons" "no"
	Option 		"ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier 	"Monitor0"
	VendorName 	"Unknown"
	ModelName 	"STN SAMTRON"
	HorizSync 	30.0 - 85.0
	VertRefresh 	50.0 - 160.0
EndSection

Section "Monitor"
	Identifier 	"Monitor1"
	VendorName 	"Unknown"
	ModelName 	"TV-0"
        HorizSync 	30-50
        VertRefresh 	60
EndSection

Section "Device"
	Identifier 	"Device"
	Driver 		"nvidia"
	VendorName 	"NVIDIA Corporation"
	BoardName 	"GeForce 8400 GS"
	BusID 		"PCI:2:0:0"
	Option          "NoLogo" "True"
       Option          "TwinView"
	Option 		"TwinViewOrientation" "clone"
	Option		"metamodes" "CRT: 1280x1024 +0+0, TV: 640x480 +0+0"        
    	Option 		"ConnectedMonitor" "CRT-0,TV-0"
	Option          "TVStandard" "NTSC-M"
	Option          "TVOutFormat" "S-VIDEO"
EndSection

Section "Screen"
	Identifier 	"Screen0"
	Device 		"Device"
	Monitor 	"Monitor0"
	SubSection 	"Display"
		Depth 24
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"Screen1"
	Device 		"Device"
	Monitor 	"Monitor1"
	SubSection 	"Display"
		Depth 24
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "AIGLX" "True"
        Option          "Xinerama" "False"
EndSection

Section "Extensions"
	Option 		"Composite" "Enabled"
EndSection
```

---

### Post by paragonconcept on 2009-03-11
Cool - i'll try it when i get home.

Thanks

---

### Post by groovietuner on 2009-04-05
FYI, S-Video is a standard def format with two separate component streams, Y and C (luminance and chromanance).  The standard's maximum resolution is 640x480.  It's only slightly better than composite video (also standard def), which carries all of the information in one stream.  To get a resolution higher than 640x480, you'll need to get to component video (YPbPr (luminance, luminance minus blue, luminance minus red), which supports up to 1080p.

Hope that helps.
Peace.

---

### Post by rickabillie on 2010-07-27
I have a workaround (after 3 days on this!) I use a regular svideo cable (the guy @ BFI said that was correct) I did not have to break a tab off.
My card is a 8400gs (nvidia)
I set up my xorg through the nvidia (195  I think) settings I use twinview, both 1024 x 768, and set the second  monitor (tv) to clone.  I save it without merging and as I reboot I  disconnect the monitor leaving only the [[COLOR=blue]_svideo_[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?p=2293879#")  out plugged in,  I reboot, get the bios splash and once linuxmint (9)  starts booting (the dots progressing as seen on tv, or you could just  count) I plug the monitor  back in and both the dfp and the svideo out work, (i use the settings overscan option to see everything on the monitor.

btw, I HATE this work-around, will prolly try to find a better card,,,
any suggestions on which to buy (~$50)?


I wonder if there is a way to get the bios to do this for me?
If I had the Nvidia cable would it just work?  Anybody got a link to the cable?
if anybody has another suggestion that might make it just work, I have included the following:

my xorg [http://pastebin.com/Ze6btxhn](http://pastebin.com/Ze6btxhn)
my xorg log [http://pastebin.com/bvnkAiBi](http://pastebin.com/bvnkAiBi)

Thanks

/rickabillie

---

### Post by JuliusRaphael on 2010-10-23
Hi! I have the same problem as TS, I've got a GeForce 8400 with S-Video and I would like to run TwinView on my TV. Problem is Ubuntu doesn't seem do detect my TV, only when I unplug my monitor the TV displays the computer. Unfortunatly when the picture is on the TV, it won't start into X. 
I've tried changing around in xorg.conf alot but it has only resulted in trouble so now I've reset it and I'm asking if someone could take a look at it and add whatever needs to be there.

Here is my xorg.conf:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.12  (buildmeister@builder101)  Fri Oct  8 13:54:10 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```


I really hope you can take your time.
Thanks!

---

