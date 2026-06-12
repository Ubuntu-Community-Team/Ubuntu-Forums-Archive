---
title: "[SOLVED] Cannot log in to KDE after attempt to change intel video driver."
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by StiltonSandwich on 2007-06-26
I have one of these notoriously tricky intel integrated graphics laptops which necessitates the use of 915resolution or the "intel" graphics driver that does the same job.

I am running Kubuntu Feisty on it.

I have been using the the "intel" driver for about two months now with no problems whatsoever at the LCD's native 1280x800 resolution. However, the "intel" driver does not appear to be as fully featured as the i810 driver, and Beryl and Compiz don't run very well on it, so I've not been using them.

The reason I've been using the "intel" driver and not the i810 one is that, when I was using the i810 one, once I had installed 915resolution in order to obtain a 1280x800 screen resolution I was unable to log in to KDE. When I changed to the "intel" driver, the problem disappeared and I was able to log in without problems.

Last night, however, I decided to try the i810 driver again, to see if I could get Beryl working. I had forgotten the problems I had before. This laptop used to work fine with the i810 driver under OpenSUSE, so I figured it should be possible to get it working. I just failed to comprehend how complicated it might be.

I reinstalled the i810 driver and 915resolution (which I had uninstalled before) ran ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and changed the video driver to i810 from intel. Then, I restarted the X-server by pressing Ctrl+Alt+Backspace.

I knew something was up when the login screen appeared - it flickered blankly about three times as if trying to get the right video mode before finally displaying the login screen at 1280x800. This is what it used to do when I had the i810 driver before. I tried logging in anyway, but it was just as I expected from past experience;  at the point where the KDE startup splash screen normally appears, it flickered in the same way as before, before returning to the login screen without any hints of a desktop appearing. The behaviour persisted after a system restart.

At this point I decided to give up and return to the intel driver - it was a bit of a whim anyway, so I wasn't too disappointed. However, upon running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` again and returning the driver to the intel one, followed by a restart of the X-server, I was greeted by the same flickering, which again persisted after a system restart. Of course, as before I can't log in to a KDE session either.

I am able to log in using the "Failsafe" option, and from there I can start most of the KDE desktop (i.e. the bits I know of)  manually from the terminal, and the screen is running at 1280x800 perfectly fine. That is how I'm running it at the moment, and indeed was how I was running it previously (albeit at a lower resolution) before I originally installed the "intel" driver.

Why might this be happening? Surely I have technically not changed anything, having reverted the one change I made?

Anyway, I decided to try a few more things. I uninstalled the i810 driver and 915resolution again, in case they were somehow being used by mistake. That didn't change anything.

Then I decided to revert to the backup xorg.conf that was made when I issued the initial command to change back to the i810 driver. That also had no effect, although to be honest there wasn't much different between them anyway, so something else must have changed outside of that.

I've since re-run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and ```
sudo dpkg-reconfigure xserver-xorg
``` several times in vain and then reverted to the backup again.

I also note that the system startup is different now. When I had a working display driver, the progress bar on the splash screen used to move the first few pixels before freezing up, then after a delay a thick white bar would appear across the entire width of the screen, partly obscuring the progress bar, then the login screen would appear after another delay. Now the progress bar works as expected, but there is the flickering before the login screen and the lack of ability to log in.

Similarly, when I shut down I now get a working backwards progress bar, whereas before I used to get a frozen one followed by some plain text and sometimes that was followed a blank screen with random characters blinking on it which seemed to max out the processor and set the cooling fan running, at which point I would turn the power off manually if it didn't seem to be getting anywhere. Now the shutdown works perfectly.

I'd much rather have the graphically flawed startup and unclean shutdown than have to manually start KDE every time I log in!

Any suggestions? For now I just want a working desktop. It doesn't have to support Beryl.

There are plenty of posts relating to these intel drivers, but they all seem to describe slightly different problems, and none of them sounds the same as mine. I suspect, however, that this may be a KDE problem anyway, but I haven't got any other desktop environments installed, though, so I can't really test that easily.

Sorry for the ludicrously long post (Scrolling pages is a pain!), but I thought it'd be better to fully describe the problem than to skimp on the details to save space.

Below are my xorg.conf files. The first is my current one, which is the same as the backup one, so should be the same as the original one that worked. The second is the one that is made when I change to an i810 driver.

I don't know if it's related, but I don't have a tablet PC or graphics tablet, and yet my xorg.conf has always referred to one. I've never removed it in case it has some other purpose, but it's always been there.

Current/backup/previous xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel i915"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i915"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

i810 xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel i915"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i915"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by StiltonSandwich on 2007-06-26
Just a small update on my situation.

If I log in using "Failsafe" as the session type and then start KDE using ```
startkde
``` (a command I only just discovered) I get the KDE startup splash, followed by a brief, tantalizing glimpse of my desktop before it reverts to the login screen again.

If I manage to fix it, I will post again with my solution.

---

### Post by StiltonSandwich on 2007-06-27
Problem solved.

It appears to have all been down to a single KDE config file, and nothing to do with X:

/home/<my user>/.kde/share/config/displayconfigrc

With that file deleted, everything seems to be back to normal.

I found the following forum topic, which is what led me to try deleting files in my .kde directory:
[http://www.linuxquestions.org/questions/showthread.php?t=532365]("http://www.linuxquestions.org/questions/showthread.php?t=532365")

If anyone else tries deleting the contents of their .kde directory, don't forget to make a backup of it first to preserve your customizations; then you can try copying each file back from the backup to the live copy in, perhaps, groups of five, restarting your session each time to see if any of them have caused the crashing behaviour, then just omit the one that caused the problem.

Now I've done this, I think I recall having done it once before, so it must be a fairly common problem.

---

