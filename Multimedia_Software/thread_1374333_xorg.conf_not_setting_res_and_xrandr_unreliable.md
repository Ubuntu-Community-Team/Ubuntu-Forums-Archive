---
title: "xorg.conf not setting res and xrandr unreliable"
date: 2010-01-06
forum: Multimedia Software
---

### Post by ralyon on 2010-01-06
<background>
I am setting up a display system that will not have a keyboard/mouse and automatically boots into gnome and starts up firefox to a display page. The page is optimized to a 720p resolution which I can set when we use a TV for the display, but is not an option if we use a monitor. I am trying to find a way to set the resolution to 720p automatically on boot up. I am always using 16x9 displays with a DVI connection (to HDMI on TVs)
</background>

I was able to get one monitor working by creating a script and setting it to load in the Startup Applications as shown:
```
#!/bin/bash
scnres="1280 720 60"
modeline=$(cvt -v $scnres | grep Modeline)
modeline=${modeline#Modeline }
xmode=${modeline#\"}
xmode=${xmode%%\"*}
actdisp=$(xrandr | grep \ connected | cut -d\  -f1)
amode=$(xrandr | grep ${xmode%%_*})
if  [ -z "$amode" ]; then
    xrandr --newmode $modeline
    xrandr --addmode $actdisp $xmode
    xrandr --output $actdisp --mode $xmode
else
    xrandr --output $actdisp --mode ${xmode%%_*}
fi
sleep 5
firefox &
```

I then came across several monitors that would add the mode with an extra "(0x107)" after the name of the modeline as such:
  *"1280x720_60.00" (0x107)    74.5MHz*
When I try and use this mode I get "xrandr: cannot find mode ..." I got around this by creating another mode in xrandr with a different name and set it like this:
```
#!/bin/bash
scnres="1280 720 60"
xmodep=\"720P\"
modelinep=$(cvt -v $scnres | grep Modeline)
modelinep=$xmodep${modelinep#M*\" }
modeline=$(cvt -v $scnres | grep Modeline)
modeline=${modeline#Modeline }
xmode=${modeline#\"}
xmode=${xmode%%\"*}
actdisp=$(xrandr | grep \ connected | cut -d\  -f1)
amode=$(xrandr | grep ${xmode%%_*})
if  [ -z "$amode" ]; then
    xrandr --newmode $modeline
    xrandr --addmode $actdisp $xmode
    xrandr --output $actdisp --mode $xmode
    sleep 5
    xrandr
    xrandr --newmode $modelinep
    xrandr --addmode $actdisp $xmodep
    xrandr --output $actdisp --mode $xmodep
else
    xrandr --output $actdisp --mode ${xmode%%_*}
fi
sleep 5
firefox &
```

This works about half the time. The other half it will either lock X in a gray screen or it will drop back out to a login screen and will not log back in unless I disable the script and the 720p resolution is not available.

I then tried to enter this information in an xorg.conf I created with "sudo Xorg -configure" and entered in the mode information for the 1280x720 as described [in this thread]("http://ubuntuforums.org/showthread.php?t=1346125&highlight=xrandr+permanent+xorg.conf"). I also tried setting the "Modes" to "1280x720_60.00" which didn't work either. I also tried setting the "Modes" to "1024x768" which is an existing resolution and it did load to that resolution, so I believe the system is seeing the xorg.conf, it just doesn't like the 1280x720 configuration. I also tried setting the "Modeline", "PrefferredMode" and "Modes" to 1280x800 as I saw a reference to that being a supported resolution in the Xorg.0.log file, but this was not successful either.

I'm sure I'm missing a few things I tried along the way, but if someone could please give me some suggestions for what to try next, I would greatly appreciate it. If I can get an xorg.conf working I believe I can write a script to create a specific conf file for any monitor. I am including the xorg.conf I have been working with below. Sorry for such a long post, I tried to summarize as much as I could.

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "record"
    Load  "dri"
    Load  "dri2"
    Load  "dbe"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Modeline     "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
    Option         "PreferredMode" "1280x720_60.00"
EndSection
```

---

### Post by ralyon on 2010-01-07
I was just made aware that the xorg.conf was cut off, here is the complete xorg.conf.
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "record"
    Load  "dri"
    Load  "dri2"
    Load  "dbe"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Modeline     "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
    Option         "PreferredMode" "1280x720_60.00"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 945GME Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
    Option      "Monitor0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes     "1280x720"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes     "1280x720"
    EndSubSection
EndSection

Section "ServerFlags"
    Option    "BlankTime" "0"
    Option    "StandbyTime" "0"
    Option    "SuspendTime" "0"
    Option    "OffTime" "0"
EndSection
```

---

### Post by ralyon on 2010-01-07
SUCCESS!!!

The xorg.conf was trying to set the resolution to the VGA display instead of the DVI. Thanks to some help from the #xorg IRC I was able to get the resolution to work by adding "Monitor-DVI1" in the Device Section like this:
```
Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GME Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
	Option      "Monitor-DVI1" "Monitor0"
EndSection
```

I have also created the script to create the xorg.conf file and should work on any monitor. You need to add the desired display, width and height like so:
```
./create_xorg.sh DVI1 1280 720
```

You can find the current display with
```
xrandr | grep \ connected | cut -d\  -f1
```

The script currently has no detection for invalid input, so be very careful with your switches and it needs to be run outside of X (ie CTRL-ALT-F5). The script will however backup your current xorg.conf to xorg.conf.setresbackup jic. I might go back and make it safer later, but for now here is what I have:
```
#!/bin/bash
scnres="$2 $3"
modeline="	"$(cvt -v $scnres | grep Modeline)
resmode=${modeline#*\"}
resmode=${resmode%%\"*}
prefmode="	Option	     \"PreferredMode\" \"$resmode\""
devmonitor="	Option      \"Monitor-$1\" \"Monitor0\""
dispmode="		Modes     \"$resmode\""

sudo rm xorg.conf.new
sudo service gdm stop
sudo Xorg -configure
if [ -f /etc/X11/xorg.conf ]; then
	sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.setresbackup
fi

sed ' {
	$ a\
Section "ServerFlags"\
	Option	"BlankTime" "0"\
	Option	"StandbyTime" "0"\
	Option	"SuspendTime" "0"\
	Option	"OffTime" "0"\
EndSection\

		{
		/Depth/ a\
'"$dispmode"'
			{
			/BusID/ a\
'"$devmonitor"'
				{
				/ModelName/ a\
'"$modeline"'\
'"$prefmode"'
					{
					/[#]/ d
				}
			}
		}
	}
}' <xorg.conf.new >xorg.conf

sudo rm xorg.conf.new
sudo mv xorg.conf /etc/X11/xorg.conf
sudo service gdm start

```

---

