---
title: "TVout with ATI card (S-video)"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by jrekkedal on 2007-03-08
Trying to setup a PC I have laying around for a HTPC, and so far everything has gone swimmingly... with the exception of my TV-out.

I have an ATI radeon 9200 card, with S-video output.  When I hooked it up and logged in it was all scrambled.  Didn't take a genius to figure out it probably had to do with the refresh rate set on it.  I threw the resolution down to 640X480, but the refresh in the Preferences wouldn't change from 60hz.  I took matters into my own hands and attempted to change the xorg.conf file but the issue persists....  I'll paste what I have in my xorg.conf below so I beg the gurus to assist!

Section "Device"
	Identifier	"Radeon 9200 Pro"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"TVOutFormat" "SVIDEO"
	Option		"TVStandard" "NTSC-M"
EndSection

Section "Monitor"
	Identifier	"Television"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9200 Pro"
	Monitor		"Television"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by watson540 on 2007-03-08
No matter what setting you use, i never could get the tv out working with the open source radeon driver. I hate to say it but you need to install ati's fglrx driver. When you do that hook up both your monitor and tv and make sure they're on and junk. then do a 'dpkg-reconfigure xserver-xorg' make sure you pick fglrx for driver, it will pick out all the rest of the stuff for you, just answer all the defaults, even when it asks you for monitor info just keep hitting enter and it will work

---

### Post by sysdrum on 2007-03-08
You also should follow this guide for edgy

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by gabng on 2007-03-08
> **watson540 said:**
> No matter what setting you use, i never could get the tv out working with the open source radeon driver. I hate to say it but you need to install ati's fglrx driver. When you do that hook up both your monitor and tv and make sure they're on and junk. then do a 'dpkg-reconfigure xserver-xorg' make sure you pick fglrx for driver, it will pick out all the rest of the stuff for you, just answer all the defaults, even when it asks you for monitor info just keep hitting enter and it will work

Hi, I'm trying to achieve tv-out with this cards as well.  Related to the quoted method, I read in a lot of posts that there are gamma problems on the computer monitor.  Have you encountered this issue?

---

### Post by jrekkedal on 2007-03-08
Just wanted to let you all know that the article advised by sysdrum worked like a charm.  TV out works great and it was so simple I couldn't believe it.  Made it harder for myself I think....

---

### Post by AR_Kozz on 2007-03-09
I just posted a thread about this exact same thing only a few hours before, though noone has replied to mine yet (hey no fair! j/k)

except that I'm using the component out instead and Dapper not Edgy

I noticed that if I restart with the TV hooked up, the monitor's output is cloned perfectly on the TV all the way up until the point where X-windows starts up, then it scrambles

I thought it would be an issue in Xorg.conf not the driver, but that also makes sense 

With any luck that article for edgy may work for me too.

---

### Post by gabng on 2007-03-09
> **jrekkedal said:**
> Just wanted to let you all know that the article advised by sysdrum worked like a charm.  TV out works great and it was so simple I couldn't believe it.  Made it harder for myself I think....

jrekkedal, great to know TV out works perfectly for you!  Just one question, is 3D rendering also working nicely?  Coz I read from other posts that it's always only either one or the other that works for different methods.

---

### Post by AR_Kozz on 2007-03-09
I just got mine working (minus one remaining issue) with Envy, an alternative to the how-to in the link above that installs the fglrx driver automatically. made by tseliot, a mod here, there's download links on this board somewhere.

before I installed with Envy I couldn't get rendering to work, but once Envy was done rendering was enabled. I have a nice GUI control panel too.

---

### Post by Hasen_A on 2007-03-13
Hi guys, I followed the steps and am not able to get my TV to work. It works under Windows, so I dont know whats wrong:

here my xorg.conf:
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
	Screen         "Default Screen" 0 0
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
	FontPath     "/usr/share/fonts/X11/misc"
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

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbVariant" "nodeadkeys"
	Option	    "XkbOptions" "lv3:ralt_switch"
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
	Identifier   "P19-1A"
	HorizSync    31.0 - 64.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
Identifier "Television"
HorizSync 30-50
VertRefresh 60
EndSection

Section "Device"
	Identifier  "RADEON X800"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "EnableMonitor" "tmds1,crt1"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option "TVOutFormat" "SVIDEO"
	Option "TVStandard" "NTSC-M"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "RADEON X800"
	Monitor    "P19-1A"
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

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```




```
sudo aticonfig --enable-monitor=tmds1,crt1
``` works perfectly, but ```
sudo aticonfig --enable-monitor=tmds1,tv
``` and ```
sudo aticonfig --enable-monitor=tmds1,nocrt1,tv
``` have no result on my TV working.

---

### Post by AR_Kozz on 2007-03-15
Try using Envy instead, there's a download link on these forums. It got tv-out working for me...

Jrekkedal I use a radeon 9200 dual too, I'm wondering when you got yours to work can you play video on your tv? I got mine working with Envy but no matter what I do every video I play on the TV has almost half the image cropped off, even if it's viewed at small size in a window. If it's working for you what's your xorg.conf?

---

### Post by IanW on 2007-03-15
> **AR_Kozz said:**
> Try using Envy instead, there's a download link on these forums. It got tv-out working for me...

Jrekkedal I use a radeon 9200 dual too, I'm wondering when you got yours to work can you play video on your tv? I got mine working with Envy but no matter what I do every video I play on the TV has almost half the image cropped off, even if it's viewed at small size in a window. If it's working for you what's your xorg.conf?

You need to have both your monitor and TV running at the SAME resolution - 640x480 for S-Video.

---

### Post by FluffyBunny on 2007-05-09
I had the same problem with the video being cut off,  even with matching resolutions.
I only got it to work by using
aticonfig --ovt=disable
and restarting the x-server after that and then the video showed normal on the monitor and tv.

---

