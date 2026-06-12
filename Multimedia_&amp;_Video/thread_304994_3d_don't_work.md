---
title: "3d don't work"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by kimara on 2006-11-22
Hi!!

I cannot get 3d/opengl/dri/aiglx work.

I have tried community and fglrx driver. I have radeon 9250 and Ubuntu is Edgy.

community driver: xorg.conf

```
Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection


Section "Device"
	Identifier  "radeon 9250"
	Driver      "ati"
	Option      "XAANoOffscreenPixmaps"	
	Option       "AGPMode"       "8"
        Option       "AccelMethod"   "EXA"
        Option       "ColorTiling"   "on"	
	BusID       "PCI:1:0:0"
EndSection


Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    20.0 - 70.0
	VertRefresh  20.0 - 70.0
	Option	    "DPMS"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "radeon 9250"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Enable"
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```


```
$ glxinfo | grep render
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

```
$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(EE) AIGLX: Screen 0 is not DRI capable
```

 
FGLRX:
When using fglrx, computer goes login screen but monitor is blank.

xorg:
```
Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection


Section "Device"
	Identifier  "radeon"
	Driver      "fglrx"
	Option      "UseFBDev" "True"
	Option      "VideoOverlay" "on"	
	BusID       "PCI:1:0:0"
EndSection


Section "Monitor"
	Identifier   "lg"
	HorizSync    20.0 - 70.0
	VertRefresh  20.0 - 70.0
	Option	    "DPMS"
	Modeline "1680x1050"  119.12  1680 1728 1760 1840  1050 1052 1058 1080
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "radeon"
	Monitor    "lg"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection
```

When I used Dapper, fglrx worked like a charm.

I have looked lot a posts here and followed lot of guides but cannot get it work =(..

---

### Post by Rajiv_Nair on 2006-11-22
after uve finishd installation on fglrx drivers from ATI try running the command
> sudo aticonfig --initial --force
this replaces ur xorg.conf with da default fglrx configured xorg.conf.

---

### Post by kimara on 2006-11-23
I have already tried that, thanks.

---

### Post by daradib on 2006-11-23
Disable composite extensions to add 3d support for fglrx driver. Aiglx will not work since it requires composite extensions, so use XGL and Beryl instead.

To disable Composite extensions, add the following lines to the end of /etc/X11/xorg.conf file:

Section "Extensions"
        Option "Composite" "false"
EndSection

You will get 3D, DRI, and OpenGL support.

---

### Post by kimara on 2006-11-25
Fglrx work only if I use vga-cable, if I use dvi-cable screen is blank.

---

### Post by daradib on 2006-11-26
Your problem is quite surprising. I personally have an ATI Radeon X800 and I use DVI. There is a problem with DVI, which makes me not able to see the shut down visually. Since I was tired of the problems, I disabled usplash in grub. Go into your grub configuration file with sudo access (most people have it in /boot/grub.conf though mine is in /booot/grub/menu.ls).

Go to this section:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 ro quiet [COLOR="Red"]splash[/COLOR]
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

and remove the word splash. This disables graphical loading, but it might help have a monitor screen later.

In addition, you can also try this for fglrx drivers if you haven't already done so:

```
sudo aticonfig -overlay-type=Xv
```

You could also do:
```
sudo dpkg-reconfigure xserver-xorg
```
(This makes the old default xorg configuration) and then do
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Sorry if this didn't help you.

---

### Post by Martin A on 2006-11-26
I tried for months to get my 9250 working with fglrx.... the solution was buying an nVidia card, and I haven't heard from anyone who's successfully got a 9250 working. Sorry to be the bearer of bad news....

---

### Post by kimara on 2006-11-27
I just bought nvidia 7600GS so it doesn't matter anymore :)

I just hope I can get it work..

but thanks..

---

### Post by jamessnell on 2006-12-04
Well, I hope the situation is changing.. I've got a AGP and a PCI video card in this machine which both use the Radeon 9250 GPU.

At this point in time, I've got the two monitors connected to the PCI card and one display on the AGP running X (on 6.10) using Xinerama..

However, I too can't get OpenGL running on the fglrx driver. I am definiitely using the fglrx driver in xorg. Here's a summary of things:

```
cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX: Screen 0 is not DRI capable
(EE) AIGLX: Screen 1 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

And dmesg:
```
dmesg | grep fgl
[17179610.400000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179610.408000] [fglrx] Maximum main memory to use for locked dma buffers: 555 MBytes.
[17179610.408000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0

```

Here's my xorg.conf:
```
cat /etc/X11/xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

#       Screen          0 "mon1" 0 0
#       Screen          1 "mon2" LeftOf "mon1"
#       Screen          2 "mon3" RightOf "mon1"
        Identifier     "Default Layout"
        Screen         "Screen1" 0 0
        Screen         "Screen3" RightOf "Screen1"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Extensions"
        Option  "Composite"     "false"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
        SubSection "extmod"
                Option "omit xfree86-dga"
        EndSubSection
        Load  "GLcore"
        Load  "dbe"
        Load  "record"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "ON"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "mon1"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "mon2"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "mon3"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "dev1"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal,reverse"
        Option      "backingstore" "true"
        Option      "UserInternalAGPGART" "no"
        BusID       "PCI:0:15:0"
EndSection

Section "Device"
        Identifier  "dev2"
        Driver      "fglrx"
        BusID       "PCI:0:15:1"
EndSection

Section "Device"
        Identifier  "dev3"
        Driver      "fglrx"
        BusID       "PCI:1:00:0"
EndSection

Section "Device"
        Identifier  "dev4"
        Driver      "fglrx"
        BusID       "PCI:1:00:1"
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "dev1"
        Monitor    "mon1"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen2"
        Device     "dev2"
        Monitor    "mon2"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen3"
        Device     "dev3"
        Monitor    "mon3"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```


Any suggestions would be VERY appreciated!

Thanks

---

### Post by TeTeT on 2006-12-28
I also had problems setting 3D acceleration up on a ATI x1800. I added the composite false entry and added DRI back (forgot that I removed it before) and it works fine now. I see some difference in the modules between our xorg.confs:


```
Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
        Load  "v4l"
EndSection
```

---

