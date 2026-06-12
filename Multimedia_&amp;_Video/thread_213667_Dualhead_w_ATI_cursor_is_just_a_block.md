---
title: "Dualhead w/ ATI: cursor is just a block"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by devnulljp on 2006-07-11
I have just set up two 64bit machines w/ Kubuntu 6.06 in dualhead configurations. Unfortunately, they have ATI X1300 video cards and not nVidias.
Jumped through all the hoops in the excellent howto [here]("http://ubuntuforums.org/showthread.php?t=204910") to get ATI's proprietary driver to work.
I set up the driver with:
```
aticonfig --initial=dual-head 
```
 
It works OK with one machine with two identical monitors, but on the other, which has an Apple Cinema 20" and a 19" LCD, the cursor is just a block on the second monitor. It displays OK, windows are fine, just the cursor...
Any ideas? 

Relevant bits of xorg.conf below:

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
#For dualhead
        Option         "Xinerama" "on"
        Option         "Clone" "off"
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
        Load "dbe"
        Load "record"
        Load "vbe"
EndSection

Section "Monitor"
        Identifier   "Apple Monitor"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection
                                                                                                                                          Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
        Screen      1
EndSection

```

---

### Post by djgenesis on 2006-07-16
One of the possible problems i would have thought, is that you are using the same PCI bus for both cards.
> 
Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
        Screen      1
Try to list your devices and check which bus the second montor is under.

```

genesis@Ubuntuj:~$ lspci

0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 11)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 11)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
**0000:[COLOR="Blue"]01:00.0[/COLOR] VGA compatible controller: ATI Technologies Inc R300 AD [Radeon 9500 Pro]**
**0000:[COLOR="Blue"]01:00.1[/COLOR] Display controller: ATI Technologies Inc R300 AD [Radeon 9500 Pro] (Secondary)**
0000:03:02.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
0000:03:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 81) 
```


Anyone else?

---

### Post by sangaya on 2006-07-17
I didn't have that exact cursor problem, but I did have simular quirky issues with my x1800XT dual display on two 17" LCD monitors. The way I got it to work was to run 
[B]sudo aticonfig –initial=dual-head –screen-layout=right
sudo aticonfig –dtop=horizontal –overlay-on=1[/B]

From my xorg.conf```

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "OverlayOnCRTC2" "1"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection
```

Hope that helps! :)

---

### Post by djgenesis on 2006-07-17
I am having a similar issue.... You see, although i have set mirroring off, my screens are mirrored. When i turn xinerama on, the system uses the default xorg.conf :( I have attached my xorg.conf file and below, there is the output of lspci. 
Can anyone help ?


```


0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 11)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 11)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc R300 AD [Radeon 9500 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc R300 AD [Radeon 9500 Pro] (Secondary)
0000:03:02.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
0000:03:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 81)

```



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

#	Option 		"Xinerama" "on"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
#	Screen	1	"aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	Option	    "Clone" "off"
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
	Option	    "XkbLayout" "gb"
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
	Identifier   "PHILIPS 107E"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "Compaq"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. R300 AD [Radeon 9500 Pro]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. R300 AD [Radeon 9500 Pro Secondary]"
	Driver      "ati"
	BusID       "PCI:1:0:1"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R300 AD [Radeon 9500 Pro]"
	Monitor    "PHILIPS 107E"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
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

Section "Screen"
	Identifier "Screen2"
	Device     "ATI Technologies, Inc. R300 AD [Radeon 9500 Pro Secondary]"
	Monitor    "Compaq"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
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

---

### Post by djgenesis on 2006-07-17
And BTW, i am turning comments off :)

---

### Post by ltmon on 2006-07-18
sangaya

Can you please post the rest of your config?  When I try to set up dual-head in bigdesktop (as opposed to mirror) I just get screen corruption.

My devices look the same as yours, so I would like to see the monitor, screen and serverlayout sections.

Thanks,

L.

---

### Post by devnulljp on 2006-07-18
> **djgenesis said:**
> One of the possible problems i would have thought, is that you are using the same PCI bus for both cards.

It's a single dualhead card (with two connectors for monitors - one analog one dvi) so they're on the same pci bus.

---

### Post by jrjr on 2006-07-18
Where do you turn om onebigdesktop? I must be missing something....

---

### Post by ltmon on 2006-07-18
> **jrjr said:**
> Where do you turn om onebigdesktop? I must be missing something....

You can try
```

sudo fireglcontrolpanel

```

But it didn't work for me.  It might be because I have a fairly new model of card.

L.

---

### Post by jrjr on 2006-07-18
Thanks but I dont know if I dare at this point!
Check this thread:

[http://www.ubuntuforums.org/showthread.php?t=217920](http://www.ubuntuforums.org/showthread.php?t=217920)

---

### Post by ltmon on 2006-07-18
> **jrjr said:**
> Thanks but I dont know if I dare at this point!
Check this thread:

[http://www.ubuntuforums.org/showthread.php?t=217920](http://www.ubuntuforums.org/showthread.php?t=217920)

I wouldn't be too afraid of experimenting, as long as you make backups.  I think the ati tools also make automated backups in your /etc/X11 directory if you ever forget.

```

cp /etc/X11/xorg.conf ~/xorg.conf.bak
[/code
create a backup

If it doesn't work out, start up in "Safe Mode"
[code]
cp ~/xorg.conf.bak /etc/X11/xorg.conf

```
to restore your original settings, and restart.

---

### Post by jrjr on 2006-07-18
LOL thanks but ive done that about a gazillion times in the last 3 days!! I am really close now to having both monitors working

---

### Post by devnulljp on 2006-07-20
Follow up on my own thread - the cursor is not actually just a simple block...it's a mini version of the main screen, which I just noticed. Weird, annoying, and useless. 
On moving to the second monitor, the standard arrow cursor becomes a square (looks like 64 pixel^2) showing whatever is on the first monitor. 
Anyone else? Fix?

---

### Post by jrjr on 2006-07-20
LOL I just hit my 4th forced disk check... thats 120 reboots in 5 days!
I went through all my old xorg configs and they all do the same now but one. That one had the vesa driver in it and I had cloned monitors. The ATI control panel said something about X11 support and only gave me one tab. I went through X config again and set it to fglrx. Then the 2nd monitor was off. ATI control panel set to single. 

I found out that I had to do a sudo to change the settings in the control panel, I could not just click on it in the menu as it would not save unless sudo'ed (is that a word?)

Anyway switching to one big desktop took me back where I started. 2 monitors active. One with wallpaper, one without. Mouse only goes 1/4" onto 2nd monitor. 

Sure would like to solve this dilema cause the alternative is going to Breezy and that means starting all over again.

---

### Post by jrjr on 2006-07-20
WOHOOO!!!!

I did it... well sort of
I changed so that I could log in as root. As soon as I logged in the first time as root the big desktop works!!  I can drag windows back and forth perfectly... nice

Now, why doesnt it work as a normal user.... thats the question

---

### Post by ltmon on 2006-07-20
> **jrjr said:**
> WOHOOO!!!!

I did it... well sort of
I changed so that I could log in as root. As soon as I logged in the first time as root the big desktop works!!  I can drag windows back and forth perfectly... nice

Now, why doesnt it work as a normal user.... thats the question

Have you checked your X log?  It possibly has an permissions error listed in it.  The file is at /var/log/Xorg.0.log.  It will only log one session, and your previous session log will be in /var/log/Xorg.0.log.old.

Cheers,

L.

---

### Post by jrjr on 2006-07-20
I'm looking at it now...  what would it say exactly?
Want me to post it?

---

### Post by ltmon on 2006-07-20
> **jrjr said:**
> I'm looking at it now...  what would it say exactly?
Want me to post it?

Look for any lines that begin with "(EE)" (without the quotes) and just post them.

L.

---

### Post by jrjr on 2006-07-20
This is from Xorg.0.log


(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.

---

### Post by jrjr on 2006-07-20
And this is from .old


(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(EE) fglrx(0): Dynamic display switching not yet supported in big-desktop mode.
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb6fb8000

---

### Post by ltmon on 2006-07-20
Well none of them seem to be real problems, so possibly the error is not being reported in the log.

L.

---

### Post by jrjr on 2006-07-20
You're looking for an error that happens when a normal user logs in and the video does not cooperate right?

If I can be of any help just ask!! :-D

---

### Post by mangaman on 2006-07-21
I am having the same problem as devnulljp, but I might know the reason. I have two diffrent monitors (ViewSonic VA1912wb and a Mag 78FD) and I get the same little messed up block for a cusor on the second screen. So I read and reread the [http://gentoo-wiki.com/HOWTO_Dual_Monitors#ATI](http://gentoo-wiki.com/HOWTO_Dual_Monitors#ATI) article and got noplace. Then I tried to run fgl_glxgears and got this error:

```

\Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30

```

Then I tried fglrxinfo and got this:

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Now I know that when I installed the drivers, before I tried to get the Dual Head to work I didn't get those errors, could that be the (or at least my) problem?

Here is my xorg.conf
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
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
#For dualhead
	Option         "Xinerama" "on"
	Option         "Clone" "off"
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

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 72.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
#	Option      "EnablePrivateBackZ" "yes"
#	Option      "UseInternalAGPGART" "no"
#	Option      "Mode2" "1024x768"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
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

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
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

The options in aticonfig-Device[0] that are commented out have no affect (at least as far as the 2 forementioned errors go) when turned on or off.

Thanks

---

### Post by jrjr on 2006-07-21
Well, I went to bed and left the PC running as root. When I got up this morning I had lost the big desktop and nothing I can do will make it come back. 

There are only 5 items in System/Administration section of the menu now. The list was nearly as long as System/Preferences if I remember right. I believe Users was in there before. What I want to do is create a new user and log in to see if maybe some of the desktop stuff I changed as root made the difference. As root, before I sent to bed, I changed the theme, wallpaper, moved some taskbar items around, placed a folder on the desktop.

I would like to see if the default config of the desktop makes a difference. What is the command to create a new user? The menu item is gone.

Also, where is the config of the desktop kept? Is it one single file?

---

### Post by jrjr on 2006-07-21
I figured out how to add a user. 

Logging in as the new user I had the bigdesktop again. Since this user is not root, it does not have root privledges... obviously, so that must not have anything to do with it. It must be in the config of Gnome desktop and changing that throws things off. 

I would like to copy the config file for the Gnome desktop from this new undisturbed user into one for my old username that the bigdesktop does not work and see if that rectifys things. 

Anyone know how to do this??

[COLOR="DarkRed"]Edit - [/COLOR]
Another thing I noticed. When running as my first identity before with no big desktop, I installed Planet Penguin Racer. While this runs nice and smooth and fast, there was a control issue. The penguin would turn left with no user input. I had to hold down the right arrow to get him to go straight. 

When I first logged in as root and had the big desktop working, this problem went away. The penguin went straight and both left and right turns were available.

---

### Post by jrjr on 2006-07-21
Ok....  whew I just hit forced disk check 5 LOL

I created a new user - zz
Logging in as zz - Big Desktop worked  
I have been unable to break it as yet. Everything that I did as root last night I did one at a time and rebooted inbetween today as zz. At least everything I could think of. 

My root account was ok (big desktop and permissions) when I went to bed but not ok when I got up. Unless the cats were messing with it I thought first it had something to do with sleep mode so that was the first thing I checked.

In my new zz profile I set the screensaver to 1 minute and screen shutdown to 2 min. After a couple of minutes asleep I awoke it again and everything was fine.

Another thing I noticed, as stated above, was that the root account had lost menu items. Also, the zz account had no sound card configured or so the volume icon told me, and it was missing the same menu items as root was. 

I logged into my jack account and all the menu items worked here (luckily). Checking System/administration/Users and Groups showed me that zz had no permissions under the user priviledges tab. Enabling all the permissions turned the menu items back on for root and they now worked for zz. Also the sound card started working with zz. SOOOooooo  somehow overnight not only the big desktop stopped working for root, but root lost permissions as well. Odd eh?

Here is a list of everything that I did as zz and rebooted inbetween....

check screen sleep mode 
change wallpaper
configure evolution
change theme
unlocked the shutdown icon on taskbar
move the shutdown icon on same bar
move shutdown icon to lower bar
unlock show desktop icon
move show desktop icon
changed the color of taskbars
switch big desktop wallpaper to tile view

I will try to be observant on my actions and when (or if) it breaks again I will advise

---

### Post by jrjr on 2006-07-22
So does anyone have an idea as to why a newly created user would have the big desktop and not the other users?

---

### Post by mpastell on 2006-11-07
Add the following to your device in section in xorg.conf for both devices: 

Option "SWcursor" "true" 

With this you get proper cursors on both displays, but the cursor sometimes leaves annoying trails...

---

