---
title: "HowTo: ATi Radeon with TV-Out and 3D-gfx, fglrx drivers."
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by oleoleole on 2006-06-22
This is only tested on ATi Radeon 9550 AGP but it may be usefull for other Radeons as well. Else, sorry my english:p

After fixing the fglrx problem that came with *ubuntu, I start figure out how to get TV-Out AND 3D-gfx to work. And for now I maybe have a weak Xorg-config, but it works. 3D and TV is maybe some slow, not so bad on TV-part, but 3D is some slow, fgl_glxgears gives around 170-200 FPS on this computer (P4 2,6GHz, 1GB ram, 128MB videoram). But I guess the reason for the slow 3D is because it's running with TV-out on all the time. This config also need an external file that starts the "thing" (ex. VLC) to run in other X screen to show the movie etc. in fullscreen. Anyway, this document is only here to help you on the way, maybe it works, maybe not. But this config does the job for me, only thing I would have been better is 3D acceleration (I guess that wourd be fixed if I could be able to turn off TV-out in normal session).

I'm not going thru the config part from part, because I really don't know why it works, and what the thing inside it means. Well lots of it is logic, but it some weirdoes there I don't understand why they do things when not do do them and such:p

To start about how i fixed the fglrx to work again with Kubuntu Dapper 6.06 LTS, I installed all fglrx modules for xorg and the latest linux kernel, after that I also got the kernel-source, kernel-headers and downloaded drivers from ATI (the official drivers). When downloaded and unpacked the kernel-source and headers, I ran the ATI driver-install. Just followed the steps and it compiled and all without "installing" the driver. But I copy the fglrx-module manually into kernel-modules-dir and it worked. Just be sure you have enabled agpgart and the chipset too. What I did to copy a working fglrx-moduleinto the kernel-modules-dir was:
cp /lib/modules/fglrx/fglrx.2.6.15-25-686.ko /lib/modules/2.6.15-25-686/volatile/fglrx.ko (replace 2.6.15-25-686 with your kernel-version, "uname -r" shows you)
After that I stopped kdm: sudo /etc/init.d/kdm stop (press Alt+F1 to get to TTY showing console and login as root, or use sudo if it's unable (I'm using a very modified kubuntu, most of them are config-files from debian so I don't remember what is working in kubuntu or not:p))
And now you can load your fglrx drives with ex. modconf under the "directory" volatile, I don't remember what to write directly in console:p
If it success, you can start kdm again: sudo /etc/init.d/kdm start (and you should see the login-screen)
If it fails, try to load other chipset drivers, or more of them:p And if it's not specified in /etc/modules, then add fglrx, agpgart, and your chipset drivers.

Here is my xorg.conf file:
**NB! Use this to compare it to your own config, and make a backup. This file I think you wont use, unless if you're a dvorak-user and live in Norway or other countries using "PAL-G":p (PAL-B may alse be able to use in Norway, but it failed here).**
```

Section "DRI"
        Mode         0666
EndSection

Section "ServerFlags"
        Option      "Xinerama" "false"
EndSection

Section "Module"
        Load  "dbe"     # Double buffer extension
        SubSection "extmod"
                Option      "omit xorg-dga"   # don't initialise the DGA extension
        EndSubSection
        Load  "type1"
        Load  "freetype"
        Load  "glx"   # libglx.a
        Load  "dri"   # libdri.a
EndSection

Section "ServerLayout"
        Identifier     "crt"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerLayout"
        Identifier     "tv"
        Screen         "TV Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
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

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "no"
        Option      "XkbVariant" "dvorak"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
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
        Identifier   "COMPAQ MV920"
        HorizSync    30.0 - 96.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "TV"
        HorizSync    30.0 - 50.0
        VertRefresh  60.0 - 60.0
EndSection

Section "Device"

#    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automaticaloly
        Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9550]"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
        Option      "MonitorLayout" "CRT, NONE"
# === disable/enable XAA/DRI ===
        Option      "no_accel" "no"
        Option      "no_dri" "no"
# === TV-out Management ===
        Option      "NoTV" "yes"
# === OpenGL specific profiles/settings ===
        Option      "Capabilities" "0x00000000"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "TVStandard" "VIDEO"
        Option      "TVFormat" "PAL-G"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"

#    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
        Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9550] TV-Out"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
        Option      "MonitorLayout" "CRT, NONE"
# === disable/enable XAA/DRI ===
        Option      "no_accel" "no"
        Option      "no_dri" "no"
# === TV-out Management ===
        Option      "NoTV" "no"
# === OpenGL specific profiles/settings ===
        Option      "Capabilities" "0x00000000"
# === Video Overlay for the Xv extension ===
#        Option      "VideoOverlay" "on"
#        Option      "OpenGLOverlay" "off"
        Option      "TVStandard" "VIDEO"
        Option      "TVFormat" "PAL-G"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. RV350 AS [Radeon 9550]"
        Monitor    "COMPAQ MV920"
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
        Identifier "TV Screen"
        Device     "ATI Technologies, Inc. RV350 AS [Radeon 9550] TV-Out"
        Monitor    "TV"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1024x768" "800x600"
        EndSubSection
EndSection

```

And this is not enough to make the thing work with TV-out, because it needs an extra file that starts f.eks. VLC in other X screen. Anyway, it's an easy proces to make this just run in TV-out mode, but sometimes (it hasn't happend here yet) the overlay for the video/media-application wont work. So I did this to make a fullscreen on TV-out.

This is the file, I call it "vlc.tvout" and it's in /usr/local/bin/ path:
```

#!/bin/sh
xauth add "$(/bin/hostname)/unix:1" MIT-MAGIC-COOKIE-1 $( xauth list | egrep "$(/bin/hostname)/unix:0" | awk '{print $3}' )
exec /usr/bin/xinit /usr/bin/aterm -ut -e /usr/bin/vlc --fullscreen --loop -vo sdl "$*" -- /usr/X11R6/bin/X :1 -layout tv

```
**EDIT: To use this file you need to add this in "the right click on a file" in your file-browser. Else it wont work.**
By that I mean you open the movie-clip with "vlc.tvout"

Some of this have been taken from a site that helped me once with TV-out for nVIDIA, but I'm tired of the poor 2D graphic nvidia gives generally. My opinion though. But I don't have the URL for that site right now, sorry.

**I don't take the responsibility if something went wrong, but please ask me about things if you don't understand what i meant with something in this document. And yes, this is a very poor "HowTo", maybe not classified as it either.**

---

### Post by pclancy on 2006-06-22
I have a Radeon 9800 Pro, and I'm still having some difficulties.  The first thing I tried was to use aticonfig --dtop=clone, which gave me the correct screen on the tv, but not the correct resolution.  So whenever I moved the mouse on the monitor to a corner, the picture on the tv would shift to that corner.

So, I edited my xorg.conf:
```

Section "DRI"
	Mode         0666
EndSection

Section "ServerFlags"
        Option      "Xinerama" "false"
EndSection

Section "ServerLayout"
	Identifier     "crtt"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerLayout"
        Identifier     "tv"
        Screen         "TV Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
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
        Load  "dbe"     # Double buffer extension
        SubSection "extmod"
                Option      "omit xorg-dga"   # don't initialise the DGA extension
        EndSubSection
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
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
	Identifier   "SyncMaster"
	HorizSync    30.0 - 85.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier  "TV"
        HorizSync    30.0 - 50.0
        VertRefresh  60.0 - 60.0

EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
        Option      "MonitorLayout" "CRT, NONE"
# === disable/enable XAA/DRI ===
        Option      "no_accel" "no"
        Option      "no_dri" "no"
# === TV-out Management ===
        Option      "NoTV" "yes"
# === OpenGL specific profiles/settings ===
        Option      "Capabilities" "0x00000000"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "TVStandard" "VIDEO"
        Option      "TVFormat" "NTSC-M"

# ======== OLD OPTIONS ======
#	Driver      "fglrx"
#	Option	    "UseFBDev" "true"
#	Option	    "DesktopSetup" "clone"
#	Option      "TVStandard" "VIDEO"
#	Option	    "TVFormat" "NTSC-M"
# === TV-out Management ===
#        Option      "NoTV" "yes"

	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro" #"aticonfig-Device[1]"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
        Option      "MonitorLayout" "CRT, NONE"
# === disable/enable XAA/DRI ===
        Option      "no_accel" "no"
        Option      "no_dri" "no"
# === TV-out Management ===
        Option      "NoTV" "no"
# === OpenGL specific profiles/settings ===
        Option      "Capabilities" "0x00000000"
# === Video Overlay for the Xv extension ===
#        Option      "VideoOverlay" "on"
#        Option      "OpenGLOverlay" "off"
        Option      "TVStandard" "VIDEO"
        Option      "TVFormat" "PAL-G"

# ======== OLD OPTIONS =====
#	Driver      "fglrx"
#	Option      "TVStandard" "VIDEO"
#	Option	    "TVFormat" "NTSC-M"
# === TV-out Management ===
#       Option      "NoTV" "no"


	BusID       "PCI:3:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
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
	Identifier "TV Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro"
	Monitor    "TV"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes	"640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

If I run fgl_glxgears I get just under 1000, so I think that's working fine, but when I try to run vlc.tvout, I get the following errors:

```

pclancy@pclancy-desktop:~$ sudo vlc.tvout

X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux pclancy-desktop 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Jun 22 21:03:34 2006
(==) Using config file: "/etc/X11/xorg.conf"

(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found

(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6

(EE) fglrx(0): Hardware already been locked.

(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6

error opening security policy file /etc/X11/xserver/SecurityPolicy

/usr/bin/xinit:  No such file or directory (errno 2):  no program named "/usr/bin/aterm" in PATH

Specify a program on the command line or make sure that /usr/bin
is in your path.

waiting for X server to shut down

FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.

```

Any ideas?

---

### Post by oleoleole on 2006-06-22
> 
.....

If I run fgl_glxgears I get just under 1000, so I think that's working fine, but when I try to run vlc.tvout, I get the following errors:

```

....
/usr/bin/xinit:  No such file or directory (errno 2):  no program named "/usr/bin/aterm" in PATH
....

```

Any ideas?

You need to install or find the path to xinit and aterm, you can also choose other terminals than aterm (edit the file). And you shouldn't run this in super-user priviligies, because it should start with your user in it's own X-session.
To use this file you need to add this in "the right click on a file" in your file-browser. By that I mean you open the movie-clip with "vlc.tvout" Else it wont work. I forgot to mention that:p But it's edited now:p

---

### Post by pclancy on 2006-06-22
I made the appropriate changes (switching aterm to gnome-terminal), but now when I try to open a movie clip with vlc.tvout, nothing happens.  What do you think is the best way to debug this problem?

Thanks for the help.

---

### Post by oleoleole on 2006-06-23
[QUOTE=pclancy]I made the appropriate changes (switching aterm to gnome-terminal), but now when I try to open a movie clip with vlc.tvout, nothing happens.  What do you think is the best way to debug this problem?

Thanks for the help.[/QUOTE]

Run the file in a terminal, so you're able to see the output. The file should start in new X session, and you will maybe see a terminal in some few secs, and it jumps out again, because vlc doesn't have anything to play.
If it locks into the new X for some reason, press CTRL+ALt+BACKSPACE. This will kill the X you're watching.

---

### Post by pclancy on 2006-06-23
Ok, so I ran vlc.tvout on a file in the terminal, and I got this message: 
```

pclancy@pclancy-desktop:~$ vlc.tvout /video/file.avi
X: user not authorized to run the X server, aborting.
giving up.
/usr/bin/xinit:  Connection refused (errno 111):  unable to connect to X server
/usr/bin/xinit:  No such process (errno 3):  Server error.

```

So, like before my next instinct is to run this as super user to get passed the permission issues.  So, I added sudo to the command above, a new X session started on my monitor, but not my tv, and then quickly crashed.  Here is what it said:

```

pclancy@pclancy-desktop:~$ sudo vlc.tvout /video/file.avi
X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux pclancy-desktop 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Jun 23 17:07:07 2006
(==) Using config file: "/etc/X11/xorg.conf"

(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6
(EE) fglrx(0): Hardware already been locked.
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6

error opening security policy file /etc/X11/xserver/SecurityPolicy

Invalid argument: "sdl"

waiting for X server to shut down

FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.

```

I have the sdl plugin for vlc installed, do I need anything else?

Thanks again for your help.

---

### Post by oleoleole on 2006-06-23
> **pclancy]Ok, so I ran vlc.tvout on a file in the terminal, and I got this message: 
```

pclancy@pclancy-desktop:~$ vlc.tvout /video/file.avi
X: user not authorized to run the X server, aborting.
giving up.
/usr/bin/xinit:  Connection refused (errno 111):  unable to connect to X server
/usr/bin/xinit:  No such process (errno 3):  Server error.

```

So, like before my next instinct is to run this as super user to get passed the permission issues.  So, I added sudo to the command above, a new X session started on my monitor, but not my tv, and then quickly crashed.  Here is what it said:

```

pclancy@pclancy-desktop:~$ sudo vlc.tvout /video/file.avi
X: warning said:**
>  === CWDDC ControllerGetConfig failed: 6
(EE) fglrx(0): Hardware already been locked.
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6

error opening security policy file /etc/X11/xserver/SecurityPolicy

Invalid argument: "sdl"

waiting for X server to shut down

FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.

```

I have the sdl plugin for vlc installed, do I need anything else?

Thanks again for your help.

Looks like you have typed wrong BusID in xorg config, in your config it says BusID PCI:3:0:0 and not BusID PCI:3:0:1 that X-server find. Try that. And I think it's weird you can't run new X-session in for you own user. Maybe it's something I forgot to say... but don't remember for now either.

Anyway, specifying a file after "vlc.tvout"-command wouldn't do the trick, unless you have configured to do it. I use the "right-click on a file"-menu in konqueror. It also works with Nautilus, and I guess it works on most of the file-browsers.

Btw. I'm not sure about the SDL, but I guess you also need the libraries...

---

### Post by pclancy on 2006-06-26
I fixed my xorg.conf, but nothing was fixed.  I had XGL installed, but I was not using it, so I did a clean reinstall hoping that might clear up some of the X issues.  It got some, but I'm still left with this:
```
X: user not authorized to run the X server, aborting.
/usr/bin/xinit:  Server error.

```

What are you're permissions for xinit?  What about X?  Should I change them to execute for all?

---

### Post by oleoleole on 2006-06-26
[QUOTE=pclancy]I fixed my xorg.conf, but nothing was fixed.  I had XGL installed, but I was not using it, so I did a clean reinstall hoping that might clear up some of the X issues.  It got some, but I'm still left with this:
```
X: user not authorized to run the X server, aborting.
/usr/bin/xinit:  Server error.

```

What are you're permissions for xinit?  What about X?  Should I change them to execute for all?[/QUOTE]

-rwxr-xr-x 1 root root 10036 2006-03-20 13:29 /usr/bin/xinit

---

### Post by pclancy on 2006-06-26
I have exactly the same for xinit, I'm not sure where to go from here.  Any suggestions?  Thanks again for all of your help.

---

### Post by oleoleole on 2006-06-26
[QUOTE=pclancy]I have exactly the same for xinit, I'm not sure where to go from here.  Any suggestions?  Thanks again for all of your help.[/QUOTE]

I'm not sure really, but something tells me I did some configuring with some Xauthority files or something... sorry I can't find it out:/

---

### Post by mjziegle on 2006-06-27
Thanks for the tips.

However, from my experience, most of the options in your xorg.conf don't do anything for the fglrx driver set.  Check your /var/log/Xorg.0.log and you'll notice almost all of the options are ignored or don't do anything.  

Generally, the easiest way to get TV out is to boot with both devices connected.  Check the /var/log/Xorg.0.log file for the detected modes for each detected monitor.

For example in mine it lists

(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz

Then make sure that these modes (or the ones you want) are listed in the screen section.

For clone mode add 

Option "DesktopSetup" "Clone"

to your Device section

My barebones xorg.conf file

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
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
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
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

Section "Monitor"
        Option      "DPMS" "false"
        Identifier  "TV"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier  "Default Screen"
        Device      "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
        Monitor     "TV"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "640x480" "800x600" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

That being said has anyone figured out how to adjust the size and position of the TV screen.  I'm getting some serious overscanning with my TV which cuts off about 2 inches of the screen.  Nvidia has a nice gui utility, but ati can't figure out how to do it.  I also can't get the driver to recognize any of the modelines I put in.

-Matt

---

### Post by oleoleole on 2006-06-27
[QUOTE=mjziegle]Thanks for the tips.

However, from my experience, most of the options in your xorg.conf don't do anything for the fglrx driver set.  Check your /var/log/Xorg.0.log and you'll notice almost all of the options are ignored or don't do anything.  

Generally, the easiest way to get TV out is to boot with both devices connected.  Check the /var/log/Xorg.0.log file for the detected modes for each detected monitor.

........

-Matt[/QUOTE]

Only things that weren't loaded in my file was:
(WW) fglrx(0): Option "UseFBDev" is not used
(WW) fglrx(0): Option "NoTV" is not used
And some WACOM-shit. 

But all that removed now, and I'm looking for a working "NoTV"-option. Because I only want to use TV-OUT when I choose too, and it's always connected. But mainly I want to disable it.

---

### Post by oleoleole on 2006-06-27
I'm just posting a new and better working xorg.conf file. The changes is that it's running without TV-OUT in normal mode, and you need to use the extra file (HERE: vlc.tvout) to enable TV-OUT-mode. So it's configured as this setup: (2D+3D)+NoTV -OR- 2D+TV (3D ain't disabled, but it's a less performance with TV-OUT enabled of course:p)

```
# ATI fglrx: setup: (2D+3D)+NoTV or 2D+TV (with *.tvout-file)

Section "DRI"
        Mode         0666
EndSection

Section "ServerFlags"
        Option      "Xinerama" "false"
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
        Load  "dbe"     # Double buffer extension
        SubSection "extmod"
                Option      "omit xorg-dga"   # don't initialise the DGA extension
        EndSubSection
        Load  "type1"
        Load  "freetype"
        Load  "glx"   # libglx.a
        Load  "dri"   # libdri.a
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "no"
        Option      "XkbVariant" "dvorak"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier   "COMPAQ MV920"
        HorizSync    30.0 - 96.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "TV"
        HorizSync    30.0 - 50.0
        VertRefresh  60.0 - 60.0
EndSection

Section "Device"

# === OpenGL specific profiles/settings ===
        Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9550]"
        Driver      "fglrx"
# === OpenGL specific profiles/settings ===
        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
        Option      "MonitorLayout" "CRT, NONE"
# === disable/enable XAA/DRI ===
        Option      "no_accel" "no"
        Option      "no_dri" "no"
# === TV-out Management ===
        Option      "Capabilities" "0x00000000"
        Option      "ForceMonitors" "crt1,notv"
# =====
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9550] TV-Out"
        Driver      "fglrx"
# === OpenGL specific profiles/settings ===
        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
        Option      "MonitorLayout" "CRT, NONE"
# === disable/enable XAA/DRI ===
        Option      "no_accel" "no"
        Option      "no_dri" "no"
# === TV-out Management ===
        Option      "Capabilities" "0x00000000"
        Option      "TVStandard" "VIDEO"
        Option      "TVFormat" "PAL-G"
# =====
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. RV350 AS [Radeon 9550]"
        Monitor    "COMPAQ MV920"
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
        Identifier "TV Screen"
        Device     "ATI Technologies, Inc. RV350 AS [Radeon 9550] TV-Out"
        Monitor    "TV"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier     "crt"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "ServerLayout"
        Identifier     "tv"
        Screen         "TV Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection
```

---

### Post by oleoleole on 2006-06-27
Maybe this will help you if you get trouble with the xserver:
```
mcookie|sed -e 's/^/add :1 . /'|xauth -q
```

Else maybe this article about nvidia-cards will be helpful (looks like the basic is the same): [http://home.austin.rr.com/unlocked/tvout.html]("http://home.austin.rr.com/unlocked/tvout.html")

---

### Post by oleoleole on 2006-06-27
By the way... using "vlc.tvout" with the movieclip after it works..:
#vlc.tvout file.avi

...I still prefer to have it in the right-click in konqueror-menu:p

---

### Post by mjziegle on 2006-06-28
[QUOTE=oleoleole]Only things that weren't loaded in my file was:
(WW) fglrx(0): Option "UseFBDev" is not used
(WW) fglrx(0): Option "NoTV" is not used
And some WACOM-shit. 

But all that removed now, and I'm looking for a working "NoTV"-option. Because I only want to use TV-OUT when I choose too, and it's always connected. But mainly I want to disable it.[/QUOTE]

If your xorg.conf file has all the relevant sections setup for multiple monitors you can use the aticonfig utility to dynamically switch between devices

For example

aticonfig --enable-monitor=crt1,tv --effective=now 

will turn on both devices according to your xorg.conf setup

---

### Post by pclancy on 2006-06-28
[QUOTE=mjziegle]That being said has anyone figured out how to adjust the size and position of the TV screen.  I'm getting some serious overscanning with my TV which cuts off about 2 inches of the screen.  Nvidia has a nice gui utility, but ati can't figure out how to do it.  I also can't get the driver to recognize any of the modelines I put in.
[/QUOTE]

Anyone get this yet?

---

### Post by oleoleole on 2006-06-28
[QUOTE=mjziegle]If your xorg.conf file has all the relevant sections setup for multiple monitors you can use the aticonfig utility to dynamically switch between devices

For example

aticonfig --enable-monitor=crt1,tv --effective=now 

will turn on both devices according to your xorg.conf setup[/QUOTE]

Yeah, I figured that, but I want things most automatic as possible... I'm lazy:p

---

### Post by jurgnn on 2006-08-02
How does this conf and script work 'normally'?
I made my own xorg.conf by adding lines from your file and x starts with 1024x resolution on monitor and tv.
(I had 1600x resolution before.)

When I start video with vlc.tvout, monitor and tv goes black and after a while video starts playing at fullscreen in monitor and tv.
So thats almost ok, but shouldn't video play only in tv screen?
Also vlc.tvout doesn't start from nautilus, it only works with "sudo vlc.tvout name.avi"

Here is my xorg.conf, its bit confusing cause I don't know what all the lines do. :)
Card is radeon 9550.
```

# ATI fglrx: setup: (2D+3D)+NoTV or 2D+TV (with *.tvout-file)

Section "DRI"
        Mode         0666
EndSection

Section "ServerFlags"
        Option      "Xinerama" "false"
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
        Load  "dbe"     # Double buffer extension
        SubSection "extmod"
                Option      "omit xorg-dga"   # don't initialise the DGA extension
        EndSubSection
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
	Option	    "Device" "/dev/input/mouse1"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "false"
	Option	    "Buttons" "7"
	Option	    "ZAxisMapping" "4 5"
	Option	    "ButtonMapping" "1 2 3 6 7"
	Option	    "Resolution" "100"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"         # Change to EVENT1
	Option	    "Type" "stylus"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY

	Option	    "PressCurve" "5,0,100,50"		#hard
#	Option	    "PressCurve" "5,0,60,100"		#Firmer
#	Option      "PressCurve" "0,0,100,100" 		#Default
# 	Option      "PressCurve" "15,0,100,75"		#Firmer
	Option	    "Speed" "0.8"			#Slower relative speed
EndSection

Section "Monitor"
	Identifier   "Q910"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

#primary?
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver      "ati"
# === OpenGL specific profiles/settings ===
        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
        Option      "MonitorLayout" "CRT, NONE"
# === disable/enable XAA/DRI ===
        Option      "no_accel" "no"
        Option      "no_dri" "no"
# === TV-out Management ===
        Option      "Capabilities" "0x00000000"
        Option      "ForceMonitors" "crt1,notv"
# =====
	BusID       "PCI:1:0:0"
EndSection

#secondary?
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
# === OpenGL specific profiles/settings ===
        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
        Option      "MonitorLayout" "CRT, NONE"
# === disable/enable XAA/DRI ===
        Option      "no_accel" "no"
        Option      "no_dri" "no"
# === TV-out Management ===
        Option      "Capabilities" "0x00000000"
        Option      "TVStandard" "VIDEO"
        Option      "TVFormat" "PAL-G"
# =====
        BusID       "PCI:1:0:0"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor    "Q910"
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
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		#Viewport   0 0
		Depth     24
            Modes    "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
        Identifier     "tv"
        Screen         "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "ServerLayout"
        Identifier     "crt"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
	  InputDevice    "stylus" "SendCoreEvents"
EndSection

```

All I want is to have 1600x resolution on monitor and video scaled to fill tv screen, tips please.

---

### Post by oleoleole on 2006-08-03
> **jurgnn said:**
> How does this conf and script work 'normally'?
I made my own xorg.conf by adding lines from your file and x starts with 1024x resolution on monitor and tv.
(I had 1600x resolution before.)

When I start video with vlc.tvout, monitor and tv goes black and after a while video starts playing at fullscreen in monitor and tv.
So thats almost ok, but shouldn't video play only in tv screen?
Also vlc.tvout doesn't start from nautilus, it only works with "sudo vlc.tvout name.avi"

Here is my xorg.conf, its bit confusing cause I don't know what all the lines do. :)
Card is radeon 9550.

[config]

All I want is to have 1600x resolution on monitor and video scaled to fill tv screen, tips please.

Read thru the complete thread again, and you get more answers:p But it starts in dual-screen, clone mode.

If you can't start from nautilus, or in you own user, it's because you haven't  permission to create new X session or something. Sorry I can't help you with that. But it works here, so it's possible:p googleit.

---

### Post by jurgnn on 2006-08-04
Fixed xsession permission problem by setting allowed_users=anybody in /etc/X11/Xwrapper.config

Now it works, but not the way I want. When X starts monitor has correct resolution and tv-out is disabled, altought there is some rubbish in tv screen.
Vlc.tvout starts new session and video is in tv and monitor.

There is one error in /var/log/Xorg.0.log that bothers me.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
No matter if I set secondary card BusID to PCI:1:0:0 or PCI:1:0:1.

This is also in log:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AS [Radeon 9550] rev 0, Mem @ 0xd0000000/27, 0xdfef0000/16, I/O @ 0xc800/8, BIOS @ 0xdfec0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV350 ? [Radeon 9550] (Secondary) rev 0, Mem @ 0xc8000000/27, 0xdfee0000/16

Doesn't that show where primary and secondary cards are? Puuh, Im lost with this. :)

Here is my current config:
```

Section "DRI"
	Mode         0666
EndSection

Section "ServerFlags"
        Option      "Xinerama" "false"
EndSection

Section "ServerLayout"
	Identifier     "crt"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
EndSection

Section "ServerLayout"
        Identifier     "tv"
        Screen         "Tv Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
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
        Load  "dbe"     # Double buffer extension
        SubSection "extmod"
                Option      "omit xorg-dga"   # don't initialise the DGA extension
        EndSubSection
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
	Option	    "Device" "/dev/input/mice"  #mouse1
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "false"
	Option	    "Buttons" "7"
	Option	    "ZAxisMapping" "4 5"
	Option	    "ButtonMapping" "1 2 3 6 7"
	Option	    "Resolution" "100"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"         # Change to EVENT1
	Option	    "Type" "stylus"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY

	Option	    "PressCurve" "5,0,100,70"		#Soft
#	Option	    "PressCurve" "5,0,60,100"		#Firmer
#	Option      "PressCurve" "0,0,100,100" 		#Default
# 	Option      "PressCurve" "15,0,100,75"		#Firmer
	Option	    "Speed" "0.8"			#Slower relative speed
EndSection

#Monitor
Section "Monitor"
	Identifier   "Q910"
	Option	    "DPMS"
EndSection

#TV
Section "Monitor"
	Identifier   "TV"
        HorizSync    30.0 - 50.0
        VertRefresh  60.0 - 60.0
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9550]"
	Driver      "fglrx" #was ati
#NEW
        Option      "MonitorLayout" "CRT, NONE"

#        Option      "Capabilities" "0x00000000"
#        Option      "ForceMonitors" "crt1,notv"

	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV350 ? [Radeon 9550] (Secondary)"
	Driver      "fglrx"
#NEW
        Option      "MonitorLayout" "CRT, NONE"

        Option      "Capabilities" "0x00000000"
        Option      "TVStandard" "VIDEO"
        Option      "TVFormat" "PAL-B"

#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"

	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9550]"
	Monitor    "Q910"
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
	Identifier "Tv Screen"
	Device     "ATI Technologies Inc RV350 ? [Radeon 9550] (Secondary)"
	Monitor    "TV"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

### Post by oleoleole on 2006-08-04
> **jurgnn said:**
> 
There is one error in /var/log/Xorg.0.log that bothers me.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
No matter if I set secondary card BusID to PCI:1:0:0 or PCI:1:0:1.


Well, if it works, then this shouldn't have anything to say. Maybe it logs that in config-file when NOT using TV-out...

---

### Post by jurgnn on 2006-08-05
Ok, let me get this straight.
When I start x, I want to have crt on and tv-out off.
When I want to watch video, I run script that turns tv-out on and shows video in tv, BUT leaves crt to show original session/picture.
Is this possible?

I feel bit stupid having to ask this again, but your script doesn't do it.

---

### Post by oleoleole on 2006-08-05
> **jurgnn said:**
> Ok, let me get this straight.
When I start x, I want to have crt on and tv-out off.
When I want to watch video, I run script that turns tv-out on and shows video in tv, BUT leaves crt to show original session/picture.
Is this possible?

I feel bit stupid having to ask this again, but your script doesn't do it.

I haven't tested this, but maybe you can switch back unsing ctrl+alt+f7/f8? Else I don't know.

---

### Post by jurgnn on 2006-08-05
> **oleoleole said:**
> I haven't tested this, but maybe you can switch back unsing ctrl+alt+f7/f8? Else I don't know.
Ah, yes it does work like that.
But I see that this is not the thread for my problem, thanks for all the help, maybe I get it work like I want some day. :)

---

### Post by mirak63 on 2006-08-07
I can't figure either how to make the tv out fullscreen and get rid of the border.
I think switching to NTSC can help, I think there is a switch on the graphic card board.

---

### Post by jurgnn on 2006-08-21
EDIT: Removed useless junk.

Ok, I finally got it, with help from this thread [http://ubuntuforums.org/showthread.php?t=32244](http://ubuntuforums.org/showthread.php?t=32244)

This conf has crt and tv-out running at same time, but I didn't notice any difference in speed, in fact opengl performance is awesome with 8.28.8 drivers.

So, this is my xorg.conf
```

Section "DRI"
	Mode         0666
EndSection

Section "ServerFlags"
        Option      "Xinerama" "false"
EndSection

Section "Files"
	FontPath     "/usr/share/X11/fonts/misc"
#	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "dbe"     # Double buffer extension
        SubSection "extmod"
                Option      "omit xorg-dga"   # don't initialise the DGA extension
        EndSubSection
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
#	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
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
	Option	    "Device" "/dev/input/mice"  #mouse1
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "false"
	Option	    "Buttons" "7"
	Option	    "ZAxisMapping" "4 5"
	Option	    "ButtonMapping" "1 2 3 6 7"
	Option	    "Resolution" "100"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"         # Change to EVENT1
	Option	    "Type" "stylus"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY

	Option      "PressCurve" "10,0,90,100" 	#Default
# 	Option      "PressCurve" "15,0,100,75"		#Firmer
	Option	    "Speed" "0.8"			#Slower relative speed
EndSection

Section "ServerLayout"
	Identifier     "crt"
	Screen         "defaultscreen" 0 0
	Screen	       "tvscreen" RightOf "defaultscreen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
EndSection

Section "Device"
	Identifier  "Radeon Primary"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen 0

        Option      "no_accel" "no"
        Option      "no_dri" "no"

	Option      "Capabilities" "0x00000000"
	Option 	    "VideoOverlay"               "on"

	#Disable video overlay when opengl overlay is enabled
	Option 	    "OpenGLOverlay"              "off"

        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
	Option 	    "mtrr" "off"
EndSection

Section "Device"
	Identifier  "Radeon Secondary"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen 1

	Option 	    "DesktopSetup" "0x00000000"

        Option      "no_accel" "no"
        Option      "no_dri" "no"

        Option 	    "NoTV" "no"

#	Option 	    "TVOutFormat" "Composite"
	Option      "Capabilities" "0x00000000"

        Option 	    "VideoOverlay" "on"
	#Disable video overlay when opengl overlay is enabled
        Option 	    "OpenGLOverlay" "off"

        Option      "UseInternalAGPGART" "no"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "ForceGenericCPU" "no"
	Option 	    "mtrr" "off"
EndSection

Section "Screen"
	Identifier "defaultscreen"
	Device     "Radeon Primary"
	Monitor    "Q910"
	DefaultDepth     24
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
	Identifier "tvscreen"
	Device     "Radeon Secondary"
	Monitor    "tv"
	DefaultDepth     24

	Option 	    "TVStandard" "PAL-G"
	Option 	    "ConnectedMonitor" "TV"

	SubSection "Display"
		Depth     24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Monitor"
	Identifier     "Q910"
	Option	       "DPMS"
EndSection

Section "Monitor"
	Identifier   "tv"
        HorizSync    30.0 - 50.0
        VertRefresh  50.0 - 60.0
EndSection

```

And I use this script to run video in tvscreen:
```

#!/bin/sh
export DISPLAY=:0.1

/usr/bin/mplayer -fs -vo gl2 "$*"

export DISPLAY=:0.0

```
export DISPLAY=:0.1 makes it so that next application will be run in :0.1 screen, or something, atleast it works now. :)

---

