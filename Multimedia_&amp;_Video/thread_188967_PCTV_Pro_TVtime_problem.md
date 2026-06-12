---
title: "PCTV Pro TVtime problem"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by ales on 2006-06-04
Hi all,

when I installed, after complications with x800 gto ati, ubuntu 5.10 everithing went fine, also my TV card PCTV Pro with the great application TVtime. Now I am surprised, that Ubuntu 6.06 has not solved probôlems with the installation with Ati x800 gto.  I installed it in safe mode. What I was installing as the first was tvtime. Bu after installation application won§t run. Reason - don't know.

Ubuntu is great, but for new users it is nightmare and complicated system, because there is no easy installation like in windows. 

If someone has same problem please write.

THX

Bye

---

### Post by Jose Catre-Vandis on 2006-06-04
Need more information than "app won't run"

Have you installed the ati drivers by following the wiki binary drivers howto?

What errors does tvtime put out if you run tvtime from terminal?

What dmesg output do you get (so we can check tv card settings)?

---

### Post by ales on 2006-06-05
There is no message, I just press Tvtime from menu and nothing happens. Ati drivers are not isntalled. When I started installation of 6.06, it shown some screen, that there something with the xdriver or xorg or what it was so I installed it in safe mode and it works. 
I will try to run tvtime from console and write it in the evening here if it writes something.


A.

---

### Post by ales on 2006-06-06
This is what I got. In Breeze there was no problem why now is


dreamwalker@dreamwalker:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/dreamwalker/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

dreamwalker@dreamwalker:~$

---

### Post by brainkilla on 2006-06-06
[http://forum.ubuntuusers.de/topic/4991/](http://forum.ubuntuusers.de/topic/4991/)

Look at the bottom of the page, I believe you'll find a solution for your problem there... And yeah, Ubuntu can be complicated, especially if you are incapable of using Google properly...

---

### Post by ales on 2006-06-06
yes funny, i don§t know even the strucutre of directories. but i solved it already by that link u sent me. it works also without the option opengl overlay off

---

### Post by Loco_gr on 2006-08-22
I still got the problem.
I have ATI X1600 and PCTV Pro and whenever I try to start tvtime it says:

```

thanasis@linux:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/thanasis/.tvtime/tvtime.xml
xvoutput: Received X error: BadValue (integer parameter out of range for operation)
xvoutput: Received X error: BadValue (integer parameter out of range for operation)
Thank you for using tvtime.

```

---

### Post by Loco_gr on 2006-10-02
The problem remains and I think that it has to do with the ATI drivers. I have the 8.28.8 version of ATI drivers. The funny thing is that whenever I work with XGL tvtime is working but with low FPS.
When I enter to Gnome without XGL then the following message is apearing:

```

Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/thanasis/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```

---

### Post by Loco_gr on 2006-10-19
Anybody? 

It's so strange. Tvtime works with XGL and doesn't work when I enter to Gnome without XGL.

I am with the latest Ati drivers:
```

thanasis@linux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6065 (8.29.6)

```

I have noticed something strange in my xorg.conf file. There are two **Section "Device"** which is very strange:

```

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection


```


Here is the complete file

```


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
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
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
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
	Load  "dri"
	Load "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us;el"
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

Section "Monitor"
	Identifier   "L1920P"
	HorizSync    30.0 - 83.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "L1920P"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```


I am without TV for more than two months.
Any help would be appreciated.

---

### Post by DavidJE13 on 2006-10-23
Sorry, no help here; just to note that I have the same problem, and I also have an ATI card. I read somewhere that this may be due to a conflict with the --overlay-type=Xv setting (not sure how reliable that is though) But changing that to opengl causes my display to go black. I haven't tried with disable yet, but I'm guessing that will be similar.

Edit: btw, I get the first error

> Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/thanasis/.tvtime/tvtime.xml
xvoutput: Received X error: BadValue (integer parameter out of range for operation)
xvoutput: Received X error: BadValue (integer parameter out of range for operation)
Thank you for using tvtime.

And I also have 2 "Driver" sections in the conf file (well, 3 but one of them is expected due to dual-head setup)

---

### Post by Loco_gr on 2006-11-28
I have found something and I hope with a little help tvtime will work.
What I have done was to run the command v4l-info two times.
One time with XGL (where tvtime works) and one time without tvtime (where tvtime doesn't work).

And guess what? The output differs.
I have saved the output in two files.
One file is called xgl and the other noxgl.

run the command 
```

diff -y noxgl xgl|grep "|"

```
and here is what i get:

```

        status                  : 0x0 []                      |         status                  : 0x102 [NO_SIGNAL,NO_H_LOCK]
        signal                  : 0                           |         signal                  : 65535
        signal                  : 0                           |         signal   

```

If someone can tell me how can I change the those setting then probably tvtime will work.

Here is the complete output of **diff -y noxgl xgl**: [http://paste.ubuntu-nl.org/34627/](http://paste.ubuntu-nl.org/34627/)

---

