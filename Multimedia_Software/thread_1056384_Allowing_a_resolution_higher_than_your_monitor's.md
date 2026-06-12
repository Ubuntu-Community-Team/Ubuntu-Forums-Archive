---
title: "Allowing a resolution higher than your monitor's"
date: 2009-01-31
forum: Multimedia Software
---

### Post by db0 on 2009-01-31
I'm recently bought a HDTV which I have connected to a Dell Inspiron 6400 laptop through the VGA Out. The laptop's monitor max (and optimal) resolution is generally 1280x800 and this is automatically detected by the system. However this resolution cannot be used by the HDTV and in any case I needed a full HD resolution of 1920x1080. So initially I edited the xorg conf and modified the screen section as such

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
          SubSection "Display"
                  Modes           "1920x1080" "1280x800" "1024x768"
          EndSubSection

EndSection
```

Restarting the X server now allowed me to select this resolution and when selected the laptop screen would simply be at the normal 1280x800 and I would need to scroll around with the mouse, while the HDTV displayed it normally. All was working normally

My problem appeared the first time I rebooted without having the VGA cable connected to the TV. In that case, again I could only select the max of 1280x800 again. The HD resolution was not available. To get it back I had to connect the TV with a VGA cable and restart the X-Server.

So my question is, is there any way to make the laptop always have the 1920x1080 resolution as an option regardless of wether the TV was connected on boot or not?

---

### Post by stderr on 2009-01-31
I dont know, but does removing the other resolutions from xorg.conf help? Make sure you know how toedit a file from the command line though in case it goes wrong. I.e. The basic use of vim, emacs or nano.

---

### Post by whaevr on 2009-01-31
Nano is easy to use as an editor ctrl-x is to exit and then hit y to save changes. I've had to use it plenty of times -.-

---

### Post by db0 on 2009-02-01
Yah, I know how to use text editors. However I don't see what benefit only having the HD resolution will have as I will not be able to use the laptop in the normal way.

Anyway, I don't think it will do anything as the laptop's resolutions were available even when not defined at all in the Screen section. For example I already now have available resolutions I have not defined such as 1280x768, 800x600 etc

---

### Post by MartyBuntu on 2009-02-01
You can't just throw any resolution at a TV.
What does the TV's manual say it supports?

---

### Post by db0 on 2009-02-01
MartyBuntu, I already know which resolutions it supports, one of them is 1920x1080. The problem is that this resolution is not available for selection if I do not start the X-Server with the TV connected and running. I'd like this resolution available always so that I can caonnect the TV even after I've booted

---

### Post by db0 on 2009-02-14
I've tried removing any othe resolution from xorg.conf except 1920x1080 but still my resolution selection is stuck at max 1280x800 unless the TV is connected beforehand.

Any other ideas?

---

### Post by cefn on 2009-02-14
Can you copy your xorg.conf and the output from invoking...
xrandr
... when your tv is plugged in?

My files are inlined below. It now works after ages of apparently having the right resolution in the file, but it not being selectable because I was addressing the wrong display with my xorg.conf changes. Note the matches between LVDS and VGA in both the xrandr invocation, and xorg.conf. Also note the matches between the names of the modelines in the xrandr invocation and the names declared in xorg.conf. Lastly note that the resolutions are declared both against the monitors and against the video card, since X tries to work out which are valid based on both of these constraints.

I spent ages messing around to get my 1440x900 display to 'extend my desktop' including all kinds of spurious driver updates and video ram hacks which were unnecessary, and simply found that
...
* the virtual resolution in xorg.conf had to be large enough for the whole dual head display
* the display name in xorg.conf had to match the display name reported by xrandr
* xrandr invocations had to match both the display names and modeline names in xorg.conf
* resolutions must be declared for your video card as well as for your monitors 
* xrandr needed to be invoked from the command line to specifically position the display relative to the other, or turn off the first display, (else they are forced to try to mirror each other, possibly meaning you're locked to the lowest resolution).


If xrandr is not installed you can install it using...

> sudo apt-get install xrandr.


The modelines I generated using the gtf tool invocation like this...

cefn@cefn-linux-tablet:~$ gtf 1440 900 60
>   # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync


I now invoke particular monitor setups for work, home and portable (laptop only) using xrandr invocations like...

> 
xrandr --output VGA --mode 1280x1024_60.00 --above LVDS
xrandr --output VGA --mode 1440x900_60.00 --above LVDS
xrandr --output VGA --off

...(note the names of the modes should match the ones declared in xorg.conf too). Good luck!

cefn@cefn-linux-tablet:~$ xrandr

> 
Screen 0: minimum 320 x 200, current 1440 x 1668, maximum 1440 x 1792
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768_60.00   60.0 +
   1280x1024_60.00   60.0  
   1440x900_60.00   60.0* 
   1360x768       59.8  
   1152x864       60.0  
   1280x768_60.00   60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x768+0+900 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x768_60.00   60.0*+
   1280x768       53.0 +
   1024x768       85.0     75.0     70.1     60.0  
   1024x600_60.00   60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)

cefn@cefn-linux-tablet:~$ cat /etc/X11/xorg.conf

> 
Section "Monitor"
    Identifier      "VGA"
	# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
	Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
  # 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
  Modeline "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
	Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
	# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
	Option          "PreferredMode" "1024x768_60.00"
EndSection
Section "Monitor"
	Identifier      "LVDS"
	Modeline "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
	Modeline "1024x600_60.00"  48.96  1024 1064 1168 1312  600 601 604 622  -HSync +Vsync
	Option          "PreferredMode" "1280x768_60.00"
EndSection
Section "Device"
	Identifier      "Intel 945 GM"
	Driver          "intel"
	Option          "AccelMethod"   "xaa"
EndSection
Section "Screen"
    Identifier      "Primary Screen"
    Device          "Intel 945 GM"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1440x900" "1280x768" "1280x1024" "1024x768" "640x480"
	Virtual 1440 1792
    EndSubSection
EndSection
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Primary Screen"
EndSection

---

