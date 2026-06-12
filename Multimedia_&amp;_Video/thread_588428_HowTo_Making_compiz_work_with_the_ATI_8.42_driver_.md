---
title: "HowTo: Making compiz work with the ATI 8.42 driver (gutsy)"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by SishGupta on 2007-10-23
If you are using the gutsy repo version of compiz, it will not work by default with any fglrx driver, including the newly released 8.42.

First [install 8.42]("http://ubuntuforums.org/showthread.php?t=588383") and make sure it is working.

Then we need to whitelist the fglrx driver,
gksudo gedit /usr/bin/compiz
edit the line
```

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"

```and add 'fglrx' to the list. The list is space delimited.

I hope this helps!

---

### Post by andreeh on 2007-10-23
You might want to comment out the "T" variable too, and just add an empty variable like so:
```
T=""
```

Good luck, that did it for me.

---

### Post by kst- on 2007-10-23
Hmm I did all this but I cant get compiz to work on my X700.. here some outputs:
```
$ glxinfo | grep direct
direct rendering: Yes

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.0.6958 Release

$ cat /usr/bin/compiz | grep WHITELIST=
WHITELIST="nvidia intel ati radeon i810 fglrx"

```

By either running 'SKIP_CHECKS=yes compiz' or removing the blacklisted hardware as written above, I can get my 'compiz' to this point:

```
$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5653 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
```

here's my --->[xorg.conf]("http://www.pastebin.org/5769")

:|

Can you tell me what to do or post a working xorg.conf for your system or even an x700? Help would be MUCH appreciated!
(on a side note: when running OpenGL games - namely Q3 - I can't set gamma anymore.. whats up with this, are these problems connected in any way?)

---

### Post by ihcnet on 2007-10-23
You need to add the following sections to your xorg.conf file ```
Section "ServerFlags"
        Option "AIGLX" "on"
EndSection

``` and change where it says ```
Option "Composite" "0"
``` to ```
Option "Composite" "1"
```

---

### Post by geekphreak on 2007-10-24
I have Xpress 200M. I installed the driver, I whitelisted it, I commented out the T variable in /usr/bin/compiz, I added Composite and AIGLX sections to my xorg.conf, but whatever I do, fglrxinfo shows mesa. Subsequently, running compiz gives me a blank (white) screen. 
What do I need to do to get fglrx to behave properly?

Any help is appreciated. Thanks!

---

### Post by QuietRiot on 2007-10-24
I have the same problem, geekphreak; so any help is appreciated.
Most bizarrely of all (maybe) is that the ATI Catalyst thingy works (it did not before when I had the previous ATI drivers). Dual monitors can be setup using ATI Catalyst, etc..

Card is X1900XT 256MB
I installed after a clean re-install of Ubuntu Gutsy x86; used [Forlong's instructions]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support").

---

### Post by geekphreak on 2007-10-24
Got it!

Followed this: [http://www.guiaubuntupt.org/wiki/index.php?title=ATI_fglrx_8.42.3](http://www.guiaubuntupt.org/wiki/index.php?title=ATI_fglrx_8.42.3)
I don't speak Portuguese but it's not hard to understand.
Pretty good performance. Yay!

---

### Post by Melcar on 2007-10-24
For all those with the mesa issue, make sure all your driver devices are set to fglrx in your xorg.conf (I have two driver listings on mine that I had to manually change).
I can get Compiz to work after removing the blacklisted device IDs.  I'm now experiencing several minor issues (slow scrolling and all that), but the biggest issue is that I don't have any video playback when I enable Compiz; I just get a black screen with sound.

---

### Post by djuniah on 2007-10-25
Thank you so much for this.  The whitelist issue was the last hurdle i had in getting it to start automatically with the new divers.  Everything works amazingly now and my old express 200m is performing like a champ.

---

### Post by benner on 2007-10-25
I have the exact same issue as kst-.  i get the same outputs to the same issues.  i have the right driver and everything but it still crashes and reverts back to metacity.

*** after one last reboot, it worked.  thanks folks.

---

### Post by hqd22 on 2007-10-25
I followed the steps but I cannot get compiz to work.

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6958 Release

$ glxinfo | grep direct
direct rendering: Yes

```

When I try adding fglrx to the whitelist and when I reboot and log in, it brings me to a blank screen. I cannot see my desktop and the only way for me to see it again is to remove the fglrx from the whitelist. Another problem I am encountering is I cannot view videos anymore. When I launch a .avi or .wmv file from VLC player or any other video apps, I get a blank screen but the sounds come through.

Here's my xorg file
```


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Logitech MX1000" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Logitech MX1000"
	Driver      "evdev"
	Option	    "Name" "Logitech USB Receiver"
	Option	    "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
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
Section "ServerFlags"
        Option "AIGLX" "1"
EndSection
Section "Extensions"
        Option      "Composite" "1"
EndSection

```

Thanks for the help.

---

### Post by Icarosaurus on 2007-10-25
I noticed that something is missing at the bottom of your xorg.conf file:
```

Section "DRI"
	Mode 0666
EndSection
```

This is very important for getting write access to DRM.
I hope this can help :)

---

### Post by hqd22 on 2007-10-25
> **Icarosaurus said:**
> I noticed that something is missing at the bottom of your xorg.conf file:
```

Section "DRI"
	Mode 0666
EndSection
```

This is very important for getting write access to DRM.
I hope this can help :)

That didn't seem to do the trick. :(

---

### Post by bthoward on 2007-11-11
I find that there is no way for me to get compiz to work without installing the xserver-xgl package.  But as soon as I install that package I start having problems with my xv video output when playing in full screen.  

I also note though that my glxgears performance goes from about 1200 when running metacity and no xgl to about 3200 when running compiz and xgl.  I'd be all for compiz/xgl if it didn't messup my video output.  

For a while my work around was to just run "metacity --replace" in a run window when ever I wanted to play a video and then running compiz in an ALT F2 window after I was done.  This is pretty klunky and kludgy but it was working....  Anyone have any insight?

This is using a ATI Radeon Mobility X300 on a Dell Latitude D610.  When doing a check it does appear that direct draw should be supported.

---

### Post by qopit on 2008-01-14
Thsi is documented elsewhere, but for any who land on this thread...

For anyone trying to get compiz working with the latest ATI drivers, you should really try installing them with the envy script here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

'tis very sweet and it makes it all nice and simple for you.  To be safe (not sure if it is fully necessary) remove compiz first (sudo aptitude remove compiz) then run envy (sudo envy -g) and then reinstall compiz (sudo aptitude install compiz).  Then do the whitelisting thing mentioned above.

---

