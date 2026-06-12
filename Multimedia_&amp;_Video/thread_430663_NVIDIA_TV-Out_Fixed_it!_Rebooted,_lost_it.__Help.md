---
title: "NVIDIA TV-Out: Fixed it! Rebooted, lost it.  Help"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by w1llywonka on 2007-05-02
Today I finally got NVIDIA's TV-Out to work properly, then I rebooted and it stopped working again.  I am following this guide:  HOWTO: NVIDIA TV-OUT for Newbies  [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

When Iogon to Ubuntu the picture always displays on my TV, but it is black and white and very distorted (the desktop picture is split in 3 and zig-zagged).

I think it is because xorg.conf thinks that my TV is a CRT.  When I go into X Server Display Configuration it shows me that I have my monitor, CRT-1 (has the settings I set for the TV), and TV-0 (disabled).  The one time it worked it only showed me two displays my monitor and TV-0.  

I am really lost and have been trying to fix this for weeks.  I am new to Ubuntu so any help is appreciated.  Alberto if you are out there,  potrebbe aiutarmi?  Relevant files attached, thanks in advance.

---

### Post by bowmanr on 2007-05-02
Scrub this ... missed this at the end :

<SNIP>
Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "TV-0" # "Monitor[1]"  
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_50" 
       	EndSubSection    
EndSection
</SNIP>


Sorry.

-------------------------------------------



Hi,

I _think_ your Screen nodes Device option is pointing to the wrong thing ...

<SNIP>
Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
 	# Option          "IgnoreEDID" "True"
	Screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	BusID           "PCI:3:0:0" # adjust using 'lspci' or cat /proc/pci 
   	Option          "TVOutFormat" "SVIDEO" #or Composite 
   	Option          "TVStandard" "NTSC-J" #or NTSC etc 
   	Option          "ConnectedMonitor" "TV-0" # "Monitor[1]"  
	# Option          "IgnoreEDID" "True"
   	Screen 1 
EndSection

Section "Screen"
    Identifier  "Screen[0]" 
    Device      "Device[0]" 
...
Section
</SNIP>

The Device being asked to use is the non-TV device.

Try setting this ...

Section "Screen"
...
    Device "Device[1]"
...
EndSection

Maybe that will help??

All the best
Robert

---

### Post by w1llywonka on 2007-05-02
Hi Robert, 

Could you please write this out again, as I am little confused?

I have two Section Screen's, are you referring to the first or the second that I should change?

Guessing, I changed the first Section "Screen" from: 

*Before*
Section "Screen"  
    Identifier  "Screen[0]" 
    Device      "Device[0]" 
    Monitor     "CRT" # Monitor[0]" 

*After*
Section "Screen"  
    Identifier  "Screen[0]" 
    Device      "Device[1]" 
    Monitor     "CRT" # Monitor[0]" 

This made the TV-Out display correctly in color, but it also stopped my computer monitor from working (no display), so no dice.  

Also I changed the TV-0 thing to just TV, I was trying that out for a second.

---

### Post by bowmanr on 2007-05-03
Morning,

Ok. Sorry. You may notice, but I edited my post. This is because I was a little silly and did not read the full xorg.conf before commenting, and then noted the second screen section. My mistake. Very silly. Sorry about that.

However, good news you got TV out (i.e the hardware is fine!!). But ... it sounds like you would like to have both the monitor and the TV outputs working at the same time? True??

In which case, TwinView is your friend.

Here are some links I used to get my TwinView working on my FX5200 recently ...

* some comments on TwinView in general : <<http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html>>

* combining TwinView and TV out : 
    <<http://www.schotty.com/wordpress/?page_id=7>>
    <<http://en.wikibooks.org/wiki/NVidia/Twin_View#TV-out_with_TwinView>>

I will post my xorg.conf later when I get home. However, I found that with the TV out I had to peg the resolution at 1024x768 because I found that the metamodes did not quite do what I wanted. Basically, the TV showed the top left hand 1024x768 pixels of the 1280x1024 desktop ... if that makes any sense. Personally, my box is for MythTV and I only ever use the monitor out for maintenance, so am not concerned about sticking the monitor desktop at 1024x768. Also, I use the 'clone' option so that when I was installing MythTV, what I saw on the screen and got working was what the TV out displayed. 

Regards
Robert

---

### Post by w1llywonka on 2007-05-03
I read your advice and hesitated to try the Twinview way after trying so long with this particular method, but unbelievably all I did was restore my original xorg.conf and paste these lines:

    Option          "CursorShadow" "on"
    Option          "TwinView"
    Option          "TwinViewOrientation" "Clone"
    Option          "MetaModes" "1024x768,1024x768"
    Option          "ConnectedMonitor" "CRT, TV"
    Option          "TVStandard" "NTSC-J"
    Option          "TVOutFormat" "SVIDEO"

into my device section and it worked.  I can also switch from clone to other arrangements via the Nvidia XServer Settings Program and Beryl works no problems (if you try Beryl with 2 screens it returns an error message.)  Brilliant, thanks for your help.

---

### Post by bowmanr on 2007-05-03
Excellent news!! Glad to help.

It's a bit of a mute point now, but as promised (and it may help someone else in the future) :

<file xorg.conf>
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

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
# RAB 20070325 0710 -- for VNC
    Load           "vnc"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
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
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"

#RAB 20070331 1015 -- for tv out
	Option "HorizSync" "tv: 30-50"
	Option "VertRefresh" "tv: 50"
	Option "TwinViewOrientation" "clone"
	Option "ConnectedMonitor" "crt, tv"

EndSection

Section "Screen"

    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
#RAB 20070325 0710 -- for VNC
    Option         "SecurityTypes" "VncAuth"
    Option         "UserPasswordVerifier" "VncAuth"
    Option         "PasswordFile" "/root/.vnc/passwd"

#RAB 20070331 1015 -- for tv out
	Option "TwinView"
#	Option "MetaModes" "tv: 800x600 @1280x1024,crt: 1280x1024; tv 800x600 @1024x768, crt: 1024x768; tv 800x600, crt: 800x600; tv: 640x480, crt: 640x480"
	Option "TVStandard" "PAL-I"
	Option "TVOutFormat" "SVIDEO"
	Option "TVOverScan" "0.7"

    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
</xorg>

Slightly different to yours. Don't fix what is not broke!.

Regards
Robert

---

### Post by w1llywonka on 2007-05-04
After playing a few videos though it seems like the sound and video quality is sometimes not so great on the TV.  The sound crackles loudly when I turn up the volume.  The video becomes blocky and doesn't play smoothly at times.  I've never had these problems from Windows XP when doing TV-out so I don't think it is any kind of hardware problem.  I think that some people have mentioned this tends to happen with Twinview as opposed to the other method.  Really good to have it working, but that crackling noise makes videos difficult to watch.  I will play around with it a little bit to see if I can't improve it.

---

### Post by Gotterdammerung on 2008-04-29
Hey folks, would you mind helping me fix my xorg.conf?

I manage to exhibit a image on my TV, but only a really distorted image.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
	Option		"XkbVariant"	"thinkpad"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	Option         	"AllowGLXWithComposite" "True"
	Option		"NoLogo" "True"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Device[1]"
	Driver		"nvidia"
	Option		"TVOutFormat" "Composite" 
	Option		"TVStandard" "PAL-M" 
	Option		"ConnectedMonitor" "TV" 
	BusID		"PCI:1:0:0" 
	Screen		1
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Monitor		"Monitor[0]"
	Device		"Device[0]"
	Defaultdepth	24
	
	Option         	"AddARGBGLXVisuals" "True"
	Option		"DisableGLXRootClipping" "True"
	
	SubSection     "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen[1]"
	Monitor		"TV"
	Device		"Device[1]"
	Defaultdepth	24

	SubSection     "Display"
		Depth       24
		Modes      "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 0	"Screen[0]"
  	Screen 1	"Screen[1]" RightOf "Screen[0]"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection
```

My system is a laptop with Nvidia 8600M graphics board running 8.04.

---

### Post by Gotterdammerung on 2008-05-07
up

---

