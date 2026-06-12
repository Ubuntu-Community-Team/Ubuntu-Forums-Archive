---
title: "Edgy Nvidia problems- Need Help"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by gabrieliscool on 2006-10-23
I recently installed Edgy RC on my computer. But since ubuntu doesn't come with Nvidia proprietary drivers, I Removed my Nvidia GeForce4 MX440 PCI video card. Today I decided to hook up the card. I downloaded the Linux driver (version 1.0-9625) from Nvidia, and installed the corresponding Linux headers. I Installed the card (BusId PC1:1:0:0), installed the drivers, etc. Everything Worked.
I rebooted, just to make sure everything worked accordingly, only to be welcomed by a message telling me that x had crashed (The Kernel Interface Is Version 1.0-7184 and I had version 1.0-9625).  I tried to see what was wrong and to correct these problems, but my attempts were futile. A few second later i had an idea. If I re-installed the driver, It might provide a temporary fix. so I tried it... and It Worked!

I Need to Find A way to Make it keep the settings.
you're my only hope.

thanks

---

### Post by phend-one on 2006-10-23
This thread might be in the wrong section.

Anyways, I'm experiencing similar problems with my GeForce 440 MX (AGP). I get the X error too. Not sure what to do but wait for a better release?

---

### Post by gabrieliscool on 2006-10-23
Are you Also Having problems With The Way GTK Draws themes?

---

### Post by tseliot on 2006-10-23
uninstall the beta by following this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#HOW_TO_UNINSTALL_THE_DRIVER_.28FROM_METHOD_2.29](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#HOW_TO_UNINSTALL_THE_DRIVER_.28FROM_METHOD_2.29)

then install the stable driver as described in Method 1 or Method 2:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by hellblade on 2006-10-23
Try removing linux-restricted-modules packages and then reinstalling the binary nvidia drivers to see if that helps.

---

### Post by gabrieliscool on 2006-10-26
It still doesn't work, and I don't want to remove linux-restricted-modules because it would kill my wifi aka only internet connection.

I'll just wait till edgy goes gold and see what happens

---

### Post by tseliot on 2006-10-26
> **gabrieliscool said:**
> It still doesn't work, and I don't want to remove linux-restricted-modules because it would kill my wifi aka only internet connection.

I'll just wait till edgy goes gold and see what happens

I have read your post again and I think to know what your problem is.

Try following point 10 and point 11 of Method 2 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#METHOD_2)

---

### Post by ato on 2006-10-26
Open /etc/default/linux-restricted-modules-common
and add nv module
```
DISABLED_MODULES="nv"
```

Otherwise, the default nvidia kernel module load on next reboot.

---

### Post by DigitalDuality on 2006-10-26
lol what the hell are you supposed to do when you can't get into x?

---

### Post by tseliot on 2006-10-26
> **DigitalDuality said:**
> lol what the hell are you supposed to do when you can't get into x?

Using a command line text editor such as vim or nano, perhaps?

Or browsing the web with linxs?

---

### Post by Mickeysofine1972 on 2006-10-26
Hi

I have a GF4 440 MX too and can only see a black screen when X starts.

I tried doing the CTRL+ALT+F1 thing but that doesn't work either.

I managed to edit the xorg.conf by starting in single user mode but that still  means I'm stuck with vesa as my driver.

It was working fine with the beta driver for the last few weeks until I did and update yesterday!

The update was done 9am GMT then I didn't restart until 11pm GMT only to find that my X server was goosed!

Mike

---

### Post by gabrieliscool on 2006-10-27
I Shall Do It Again to see if it works.

---

### Post by Mickeysofine1972 on 2006-10-27
Does anyone remember what those updates were in the last 48 hours before the release?

If you do and you know how to rollback the old version please post so I can try.

All I can remember is there was one for Usplash and maybe some libs but I cant remember what.

Mike

---

### Post by tseliot on 2006-10-27
Try this:
```
sudo nvidia-xconfig --no-composite
```

and restart the Xserver

---

### Post by Mickeysofine1972 on 2006-10-27
Did that and no joy ](*,) 

Like I say, It was working fine all the time until Wednesday night when I restarted the system. This has been working fine since the release of the beta drivers, I was actually amazed at how easy it had installed and worked along with beryl. After Wednesday night it doesn't start.

The only things that have changed since then are the updates that where applied during that last 48 hours before the release.

Mike

---

### Post by katzman on 2006-10-27
this would be a little random but check that you don't have the eeprom module loaded as that caused a very similar problem with my computer

---

### Post by Mickeysofine1972 on 2006-10-27
How do I do that?

would that have been added during the since Wednesday?

Mike

---

### Post by katzman on 2006-10-27
well as i said it would be random if that is the case but similar symptoms. use
lsmod|grep -i eeprom
to see if it is loaded and if it is use
modprobe -r eeprom
to unload it and see if X will run with the drivers.

---

### Post by gabrieliscool on 2006-10-27
I GOT IT TO WORK

...well, sort of.

You have to use the vesa driver, Unfortunately.

---

### Post by gabrieliscool on 2006-10-29
Yeah!
Woohoo!

How I got my nvidia geforce4 mx440 to work
sudo dpkg-reconfigure xserver-xorg
select the vesa driver
after you are done reconfiguring it,
sudo /etc/init.d/gdm start
add tseliot's unstable edgy eft 32bit nvidia repo in the System>Administration>Software Sources deb [http://albertomilone.com/drivers/unstable/edgy/32bit](http://albertomilone.com/drivers/unstable/edgy/32bit) binary/
open synaptic, refresh the list
install the nvidia drivers
soon you might see the update button in the notification area, if you do, click it and install the updates
reboot into cli mode(safe mode)
do a sudo dpkg-reconfigure -phigh xserver-xorg
select the nvidia driver
reboot

Edit: Including Modelines Isn't necessary 95% of the time, you only include them if your monitor is special/cheap/from 1994/trash or an LCD monitor made from an obscure brand that nobody's ever heard of from china.

---

### Post by LCmidas on 2006-10-29
thank you, gabrieliscool.

i used your method on my geforce4 440 go, and X started,finally. or i think it did. problem is, i hear the ubuntu startup sound and can even log in...but the screen is black.

back to nv until i get this worked out. at least now i don't get the "x failed" message. :)

---

### Post by tseliot on 2006-10-29
> **LCmidas said:**
> thank you, gabrieliscool.

i used your method on my geforce4 440 go, and X started,finally. or i think it did. problem is, i hear the ubuntu startup sound and can even log in...but the screen is black.

back to nv until i get this worked out. at least now i don't get the "x failed" message. :)
Follow point 16 of the problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION)

---

### Post by gabrieliscool on 2006-10-29
> **LCmidas said:**
> thank you, gabrieliscool.

i used your method on my geforce4 440 go, and X started,finally. or i think it did. problem is, i hear the ubuntu startup sound and can even log in...but the screen is black.

back to nv until i get this worked out. at least now i don't get the "x failed" message. :)

I always forget something, damn! ](*,) 

well, in my xorg.conf file, I don't include any modelines because they aren't necessary in 95% of the time. :cool:

---

### Post by LCmidas on 2006-10-29
I have tried, that, too, tseliot. still drums in the night.

previously (when it still worked), the vsync rate was 60 and hsync 75 @ 1600x1200

so added the "UseEDID" "false" and then set the modes to be "1600x1200_60"

so it looks like this:
Depth         1
Modes         "1600x1200_60"

..and so on...

not sure if i did this right. adding a modeline didn't help either.

---

### Post by gabrieliscool on 2006-10-29
> **LCmidas said:**
> I have tried, that, too, tseliot. still drums in the night.

previously (when it still worked), the vsync rate was 60 and hsync 75 @ 1600x1200

so added the "UseEDID" "false" and then set the modes to be "1600x1200_60"

so it looks like this:
Depth         1
Modes         "1600x1200_60"

..and so on...

not sure if i did this right. adding a modeline didn't help either.

maybe if you don't include modelines at all, i could work? it worked for me.

---

### Post by gabrieliscool on 2006-10-29
let me show you my xorg.conf

---

### Post by gabrieliscool on 2006-10-29
here, take a look, btw, It's a PCI video card that's why it's BusId PCI:1:0:0, yours will be different

> **gabrieliscool said:**
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce4 MX440"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce4 MX440"
	Monitor		"Generic Monitor"
	DefaultDepth	24

# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
#    Option "DisableGLXRootClipping" "True"

	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by LCmidas on 2006-10-29
here's my xorg.conf ..well, the important bits anyway. a lot of the commented out stuff has been uncommented, to no avail.

Section "Module"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

...

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
#	Option		"UseFBDev" "true"
#	Option		"RenderAccel" "true"
#	Option		"TripleBuffer" "true"
#	Option		"AllowGLXWithComposite" "true"
	Option		"UseEDID" "False"
#	Option		"IgnoreEDID" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	75-75
	VertRefresh	60-60
#	Modeline	"1600x1200" 160.96 1600 1704 1880 2160 1200 1201 1204 1242 -HSync -Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
#	Option		"ExactModeTimingsDVI" "true"
#	Option		"UseEdidDpi" "false"
#	Option		"ModeValidation" "NoVesaModes, NoDFPMaxSizeCheck"
	DefaultDepth	24
	Option 		"AddRGBGLXVisuals" "True"
	Option		"DisableGLCRootClipping" "True"
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by gabrieliscool on 2006-10-29
hmm you got junk in you xorg.conf file.

is it a laptop?

---

### Post by gabrieliscool on 2006-10-29
> **gabrieliscool said:**
> hmm you got junk in you xorg.conf file.

is it a laptop?

if it is an LCD, the max resolution is too high, do you understand now?

---

### Post by ronacc on 2006-10-29
I took your advice about disabling nv and that fixed my problem with the nvidia driver (9625beta, it works fine). now only about 2,000 others with edgy , I moved up from dapper  3 days ago and still haven't got everything working as before but at least now  i've got a decent screen to work with. 
 To Digitalduality do what I do, keep a puppy linux cd handy you can boot the cd and mount ANY drive on your system and access your config files or anything else you need to to back out of your foulups all from the comfort of a gui ( I have lots of practice I can screwup a brick).

---

### Post by LCmidas on 2006-10-29
it is indeed a laptop, and that reso and refresh rate have worked in the past.

---

### Post by gabrieliscool on 2006-10-29
we both have similar xorg.conf files, are you using a live cd?

---

### Post by LCmidas on 2006-10-29
no. i upgraded from dapper.

---

### Post by gabrieliscool on 2006-10-29
> **LCmidas said:**
> it is indeed a laptop, and that reso and refresh rate have worked in the past.

maybe you can use mine's, the main things look the same

---

### Post by phend-one on 2006-11-08
Anyone know how to install the newest drivers with the GeForce 440mx?

---

