---
title: "Intel 965G (GMA X3000) Graphic Problem"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by cbsim on 2007-05-02
Hi, I just installed Feisty Fawn and everything is fine except the graphic. I noticed some tearing on video playback (not deinterlace) and the graphic performance is poor compare to Windows. I already tried both the xserver-xorg-video-i810 and xserver-xorg-video-intel driver. Anyone had the same problem here and is there any solution?

_xorg.conf_
Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82G965 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"L196WTQ"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82G965 Integrated Graphics Controller"
	Monitor		"L196WTQ"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
                Modes           "1440x900"
                ViewPort        0 0
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

_glxinfo_
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: SGI
client glx version string: 1.4
GLX version: 1.2
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965G 4.1.3002
OpenGL version string: 1.4 Mesa 6.5.2

---

### Post by cbsim on 2007-05-04
Bump!

---

### Post by ACGilbert on 2007-05-06
Here's my xorg.conf.
It's from a desktop that I just got working.
I don't play DVDs on it, but Flash 9 works O.K.
Just discovered Windows Media files (WMA extension) acting weird though.
Totem opens, then closes without playing the file.
May be a separate issue from XGL, 3D, and Beryl which appear to be working fine.
Hope this helps,
AC

xorg.conf

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "i2c"    # added per tip
    Load           "ddc"
    Load           "dbe"    # added per tip
    Load           "dri"    # added per tip
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Samsung SyncMaster 712n"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Driver         "intel"
    Option         "XAANoOffscreenPixmaps" "True"     # added per tip
#   Option         "AddARGBVisuals"  "True"
#   Option         "TripleBuffer"  "True"
#   Option         "RenderAccel"  "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Monitor        "Samsung SyncMaster 712n"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals"  "True"
    Option         "AddARGBVisuals"  "True"
    Option         "UseFBDev" "True"
    Option         "AllowGLXWithComposite"  "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"    # added section per tip
    Mode 0666
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by cbsim on 2007-05-07
Thanks, I will give it a try!

---

### Post by cbsim on 2007-05-09
Too bad, it is still the same, it doesn't work! :(

---

### Post by cbsim on 2007-05-11
Bump!

---

### Post by shanepardue on 2007-05-15
I have experienced the same problem and have not found any solutions.

---

### Post by cbsim on 2007-05-16
Now I also notice there are some missing texture when running windows games using wine, is there a problem with my driver or configuration? :confused:

---

### Post by cbsim on 2007-05-19
Bump!

---

### Post by cbsim on 2007-05-21
Bump!

---

### Post by rabossa on 2007-05-24
Hi!

I recently bought a ASUS P5GC-MX MainBoard, with a **82945G/GZ Integrated Graphics Controller**.
Furthermore, my monitor is a LG Flatron L192WS (19'' Widescreen ).

With the default feisty configuration on my desktop computer it gets a 1280x1024 Resolution, where my TFT should have 1440x900. 3d acceleration is working fine, except the deinterlace video.
 ( I can't watch videos if Compiz or Beryl is running. )

I wish to get 1440x900 correct resolution, with deinterlace and 3D Acceleration running. 
[ATTACH]33338[/ATTACH]

Here is my actual xorg.conf file running.


Any help?

---

### Post by snoop on 2007-05-24
> **rabossa said:**
> Hi!

I recently bought a ASUS P5GC-MX MainBoard, with a **82945G/GZ Integrated Graphics Controller**.
Furthermore, my monitor is a LG Flatron L192WS (19'' Widescreen ).

With the default feisty configuration on my desktop computer it gets a 1280x1024 Resolution, where my TFT should have 1440x900. 3d acceleration is working fine, except the deinterlace video.
 ( I can't watch videos if Compiz or Beryl is running. )

I wish to get 1440x900 correct resolution, with deinterlace and 3D Acceleration running. 
[ATTACH]33338[/ATTACH]

Here is my actual xorg.conf file running.


Any help?

You can try to install a package called 915-resolution. I believe this will let you have 1440 resolution.

---

### Post by cbsim on 2007-05-25
For me installing the xserver-xorg-video-intel driver solved the resolution (1440x900) problem! ;)

---

### Post by cbsim on 2007-05-27
No solution yet? Bump!

---

### Post by cbsim on 2007-05-29
Bump!

---

### Post by cbsim on 2007-06-01
Bump!

---

### Post by snoop on 2007-06-02
I believe you can download the drivers from here : [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

---

### Post by tseliot on 2007-06-02
> **cbsim said:**
> Bump!

the intel driver 2.0 might solve your problem however is not included in Feisty. Gutsy will have it.

---

### Post by cbsim on 2007-06-08
Problem solved, just buy yourself a Nvidia or ATI graphic card, install the proprietary driver, no compilation is needed, and don't ever bother with the open source driver thing ever again, it is just wasting time, tried a few Intel 965G PCs and the results still the same, all the drivers available as default or in the repository definitely doesn't work as it should and a browse to the intellinuxgraphics download page show you some compilation steps that hardly work, whats the point of open source when you can't install and get it work easily, people don't really care whether it is closed or open source, as long as it work and install easily especially for beginner like me, just my humble opinions, anyway thanks for the reply. :)

---

### Post by starscalling on 2007-08-01
roughly the same point as using nvidia later cards in vista
to have fun dealing with the headaches :P

---

### Post by ntlam on 2007-11-05
It seems the xserver-xorg-video-intel driver helps a lot. It fixed my 82945G/GZ Integrated Graphics to get 1440x900 resolution

---

### Post by fondle-em on 2007-11-06
The new "intel" driver in Gutsy has done little (if anything) to fix the tearing that plagues video playback on my Dell 1420n, which shipped with 7.04 and got upgraded to 7.10 in an attempt to make the tearing stop.  I can't believe this problem still hasn't been fixed, considering it affects Dell machines where Ubuntu comes pre-installed.

---

### Post by ilkkal on 2007-12-23
EDIT: Sorry, I posted on a wrong topic.

---

