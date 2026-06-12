---
title: "Twinview Xorg.conf help"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by flexgrip on 2006-12-12
Hello,

I have installed the latest Nvidia driver (9631) and Im on Edgy 32bit.

I am trying to get my LCD on the left (Gateway XXXX) and my CRT on the right to run in twinview. I have followed the how to's on Twinview and edited my xorg.conf. I have also tried to define each screen in different sections although I have been told that I shouldn't have to and the Nvidia-settings utility should automagically set everything up.

When I try to enable twinview on my LCD in the Nvidia-settings applet it says this: "Failed to associate display device 'Gateway FPD1730' with X screen 0.  TwinView cannot be enabled with this combination of display devices."

I have no clue where to start and it seems I have edited xorg.conf a million times. Here is is though, and thanks for your time:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen 1" 0 0
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
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
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
    Identifier     "Generic Monitor 1"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "NVIDIA Corporation NV20 [GeForce3]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAGP"				"3"
	Option 		"RandRRotation"			"1"
	Option		"RenderAccel"			"1"
	Option		"AllowGLXWithComposite" 	"1"
#	Option 		"DisableGLXRootClipping" 	"1"
	Option		"NoLogo"			"1"
	Option		"CoolBits"			"1"
	Option 		"TwinView" "True"
        Option "UseEdidFreqs" "False"
	Option 		"MetaModes" "1024x768, 1024x768;"
	Option 		"MonitorHorizSync" 		"30-72"
	Option 		"MonitorVertRefresh" 		"50-135"
	Option 		"SecondMonitorHorizSync" 	"30-82"
	Option 		"SecondMonitorVertRefresh" 	"50-85"
	Screen		0
EndSection

Section "Screen"
    Identifier     "Screen 1"
    Device         "NVIDIA Corporation NV20 [GeForce3]"
    Monitor        "Generic Monitor 1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```
Like I said I have also tried to define each screen and that did not work so I went back to one of the original xorg.confs

---

### Post by markkun on 2007-05-20
I have the same problem with my Geforce 3 Ti 200

---

### Post by stijngysemans on 2007-06-01
me too.
"failed to associate display device TV-0 with X screen 0; Twinview cannot be enabled with this combination of display devices."
Geforce Ti500
and cable connected to the video card.

---

### Post by lancest on 2007-06-01
Just use Nvidia GUI program. Comes installed. Call it up with: nvidia-settings. Much easier that playing to much with Xorg. Works like a charm.

---

### Post by stijngysemans on 2007-06-02
I did it using the nvidia program!

---

### Post by Nythain on 2007-06-02
i think your problem might have something to do with you not telling it you have a DFP (digital flat panel) monitor connected to the card

Option    "ConnectedMonitor" "CRT,DFP"
or
Option    "UseDisplayDevice" "CRT,DFP"
one of those lines might help you but im not 100% sure

---

### Post by stijngysemans on 2007-10-26
after upgrade to gutsy it still displays the same error message :(
"Failed to associate display device 'TV-0' with X screen 0.  TwinView cannot be enabled with this combination of display devices."

---

