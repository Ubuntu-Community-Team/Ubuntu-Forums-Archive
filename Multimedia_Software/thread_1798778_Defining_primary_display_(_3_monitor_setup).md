---
title: "Defining primary display ( 3 monitor setup)"
date: 2011-07-06
forum: Multimedia Software
---

### Post by Spade12 on 2011-07-06
Hey guys, I have a Radeon HD 5830, running 3 monitors on 10.10 64bit with the 10.6 video driver.

The three monitors ( from left to right ) : 

DFP1 : 1152x2048
DFP2 : 1920x1200
CRT1 : 1360x768

The problem I'm having is getting the middle monitor to be the primary one. 

Running 
xrandr --output DFP2 --primary

puts the panel on the middle screen but my docky and icons stay on the left screen.  

Flash videos also open up on the portrait left monitor which looks awful.

Ideally I would like the icons on DFP1, docky on P2 and flash videos to open on P2.  But I would definitely settle for everyone to be on the middle screen and drag it around as I please.

Heres my xorg.conf :

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1200"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1152 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "3072 16"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1360x768"
EndSection



Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "LeftOf"
	Option	    "Rotate" "right"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   4432 2081
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Spade12 on 2011-07-07
bump plz

---

### Post by Spade12 on 2011-07-09
anybody?

---

### Post by Blasphemist on 2011-07-09
Don't you hate it when nobody figures they can help. I'll take a stab. Here are some notes on me trying to figure it out. I run dual monitors so I've worked on some of this before for myself and others.
> Configuring using xorg.conf.d (Ubuntu 10.04 and newer)
Files ending in *.conf in the /usr/lib/X11/xorg.conf.d/ directory (NOTE: will be changed to /usr/share/X11/xorg.conf.d for 10.10) are automatically loaded by X at start prior to reading the xorg.conf. These files can each contain one or more Sections in the same format used by xorg.conf.

Users can continue making custom configuration in /etc/xorg.conf as usual; the .conf snippets are mainly there for the distro or hw vendor to ship default InputClass rules and custom overrides.
I found this at this link. [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html) As you can see the default monitor is set near the bottom in what I have highlighted and yours doesn't have those lines.
> 2.2. statically setup in xorg.conf

RandR1.2 configuration in xorg.conf is based on per monitor. So you need write a 'Monitor' section for each output and specify these monitors in 'Device' section.

Below is a example snippet in xorg.conf.

```
Section "Device"

        Identifier      "Intel 945G "

        Driver         "intel"

 

        # Using the name of the output defined by the video driver plus the identifier of a

        #     monitor section, one associates a monitor section with an output by adding an

        #     option to the Device section in the following format:

        #     Option "Monitor-outputname" "monitor ID"

        Option          "monitor-VGA" "foo"

        Option          "monitor-LVDS" "bar"

        #Option         "monitor-TMDS-1" "dvi"

EndSection

 

Section "Monitor"

        Identifier      "foo"

       

        # specifies a mode to be marked as the preferred initial mode of the monitor

        # Option "PreferredMode"  "800x600"

        # This optional entry specifies the position of the monitor within the X screen.

        #Option        "Position" "1024 0"

        #This optional entry specifies that the monitor should be ignored

        #     entirely, and not reported through RandR.  This is useful if the

        #     hardware reports  the  presence  of  outputs  that do not exist.

        #Option "Ignore"  "true"

EndSection

 

Section "Monitor"

        Identifier      "bar"

 

        #Options LeftOf, RightOf, Above, Below specify monitors' relative position

        Option "LeftOf"  "foo"

        # This optional entry specifies  whether  the  monitor  should  be

        #     turned  on  at  startup.  By default, the server will attempt to

        #     enable all connected monitors.

        #Option "Enable"  "true"       

        #This optional entry specifies the initial rotation of the given monitor.

        #     Valid values for rotation are "normal", "left", "right", and "inverted".

        # Option "Rotate"  "left"

EndSection

 

[COLOR="Purple"]Section "Screen"

        Identifier      "Default Screen"

        Device        "Intel Corporation 945G Integrated Graphics Controller"

        Monitor       "foo"

        DefaultDepth  24

        SubSection "Display"

                Depth          24

                Modes         "1280x1024"  "1024x768"   "640x480"

        EndSubSection
[/COLOR]
EndSection

```
3. Reference
xorg.conf manual

xrandr manual

---

