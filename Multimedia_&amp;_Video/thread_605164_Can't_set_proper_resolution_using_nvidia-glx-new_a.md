---
title: "Can't set proper resolution using nvidia-glx-new and Gutsy 7.10...."
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by andybisnut on 2007-11-06
Hey everyone,

I know there's a lot of info on here about this, but I haven't found anything that has helped me.

I have Gutsy Gibbon 7.10 (clean install), an NVIDIA GeForce 6800GT, and an Acer AL1917W monitor (native res: 1440x900).

With the default settings (glx driver not enabled), my res can be set to the correct setting (1440x900) and the correct refresh rate (60 or 75 Hz). But of course I get no fancy effects. :(

Then, when I enable & install the 'nvidia-glx-new' driver and reboot, my resolution drops to about 1/2 of what it should be, and it will not let me select 1440x900. Editing xorg.conf does nothing, and using the 'nvidia-settings' applet is useless. I am able to enable the desktop effects, but I'm only running at half-resolution. It is highly frustrating.

Anyway, there you have it, in a nutshell. Has anyone had any luck with a similar setup to mine getting the glx-new driver to work with a 1440x900 monitor? Any insight or help you can give me on this issue would be much appreciated. Thanks!

---

### Post by RTrev on 2007-11-06
> **andybisnut said:**
> Hey everyone,

I know there's a lot of info on here about this, but I haven't found anything that has helped me.

I have Gutsy Gibbon 7.10 (clean install), an NVIDIA GeForce 6800GT, and an Acer AL1917W monitor (native res: 1440x900).

With the default settings (glx driver not enabled), my res can be set to the correct setting (1440x900) and the correct refresh rate (60 or 75 Hz). But of course I get no fancy effects. :(

Then, when I enable & install the 'nvidia-glx-new' driver and reboot, my resolution drops to about 1/2 of what it should be, and it will not let me select 1440x900. Editing xorg.conf does nothing, and using the 'nvidia-settings' applet is useless. I am able to enable the desktop effects, but I'm only running at half-resolution. It is highly frustrating.

Anyway, there you have it, in a nutshell. Has anyone had any luck with a similar setup to mine getting the glx-new driver to work with a 1440x900 monitor? Any insight or help you can give me on this issue would be much appreciated. Thanks!

Try running this:

```
sudo dpkg-reconfigure xserver-xorg
```

Eventually you should get to where you can choose the nvidia driver and then choose the resolution you want.

HTH!

---

### Post by andybisnut on 2007-11-06
RTrev,

Thanks for your reply. Believe me I have tried that. :) 

I have actually given up on this issue for now...I had a non-widescreen (1280x1024) LCD sitting around so I hooked that up to my Ubuntu machine. Now everything's peachy, except no widescreen...but oh well, at least I have the proper res AND desktop effects. I guess the glx-new drivers don't like widescreen too well, or something.

Thanks anyway though....

---

### Post by rajeev1204 on 2007-11-07
Have you tried the new screens and graphics gui tool to select driver and resolution etc

Its under system/administration

---

### Post by rykel on 2008-01-08
I have tried whatever is mentioned here, and STILL, I can no longer get back the 1280x800 resolution that is my laptop LCD... it worked perfectly on a fresh install of Gutsy, but after I disabled the driver through Restricted Drivers Manager and installed/uninstalled the official NVIDIA driver, the resolution is broken.

Help?

---

### Post by rykel on 2008-01-09
Hi all,

I finally gave in and decided to give ENVY a try... (prior to this, I had always been resistant to 3rd party scripts such as ENVY and Automatix)

And it works!

As an aside, I found it interesting that ENVY downloaded a whole lot of other debs in order to make the NVIDIA driver work... not sure why we need those, but now I am a happy ENVY user.   :guitar:

Get ENVY straight from Mr Milone the developer:
[http://albertomilone.com/index.html](http://albertomilone.com/index.html)

---

### Post by loyeyoung on 2008-01-25
My company ships Ubuntu preloaded on systems bundled with the AL1917W, so I've had to work through this myself. Here's what works on our product:

Edit /etc/X11/xorg.conf as root:

Delete the "Monitor" section and replace with:
```

Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	Identifier "AL1917W"
	VendorName "ACR"
	ModelName "AL1917W"
	# Block type: 2:0 3:fd
	HorizSync 31-84
	VertRefresh 56-76
	# Max dot clock (video bandwidth) 140 MHz
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1440x900"	# vfreq 60.070Hz, hfreq 55.625kHz
		DotClock	89.000000
		HTimings	1440 1488 1520 1600
		VTimings	900 903 909 926
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
EndSection
```

In your Screens section , change the Monitor line to:
```

	Monitor		"AL1917W"
```
If the Screens section has a Display subsection, remove that subsection. 

Add the following subsection to the Screens section:
```

	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
```
Save the file and restart X. 

You may have to experiment with the DefaultDepth setting. If you graphics card has enough memory, 24 will give you the best color. However, keeping 1440 x 900 (1,296,000) pixels lit up at 24 bits per pixel, 60 times a second is a lot of work for a graphics card. If you don't get good results at 24 bit depth, try backing it off to 16 and see what you get. (I have an old ATI Mach64 card in one of my machines, so I have to reduce the depth to 8 to get it to work.)

It is possible that your particular version of the AL1917W (there have been several versions manufactured) is engineered slightly different than the ones we are shipping. If the above doesn't work, you'll can do some command-line recognizance to get the info you need. Because the AL1917W has a solid implementation of EDID, you can run the utilities in the read-edid package to write your xorg.conf Monitor section for you. 

Run the following as root from the console:
```

root@hostname.dom:~/# get-edid | parse-edid >> /etc/X11/xorg.conf
```
Then edit /etc/X11/xorg.conf to remove any conflicting Monitor sections, and otherwise conform the rest of the file to the output of the section that parse-edid wrote for you. 

Just for the sake of completeness, if you run the framebuffer in the console, the following Mode section of /etc/fb.modes (provided by the fbset package) works for this monitor:
```

mode "1440x900-60"
    # D: 89 MHz, H: 55.62 kHz V: 60.07 Hz
    geometry 1440 900 1440 900 24
    timings 11236 80 48 17 3 32 6
    hsync high
    vsync high
    accel true
endmode 
```
Add the foregoing to the end of /etc/fb.modes and save it. Then issue from the command line, as root:
```

root@hostname.dom:~/$ fbset "1440x900-60"
```
You will note that "24" is at the end of the geometry line. That number is the depth parameter for the framebuffer. As when dealing with the X server, you may have to adjust that parameter down to 16 or even 8 when running off of some older graphics cards. 

Also, changing "accel true" to "accel false" will sometimes give better results, depending on your graphics card. 

I hope this is of some benefit to you. If not, feel free to contact me directly via my website, email, or phone. 

Happy Trails,

Loye Young
Isaac & Young Computer Company
Laredo, Texas
[http://www.iycc.net](http://www.iycc.net)

---

### Post by xtagon on 2008-03-03
I use a Acer AL1916W, and I've been having the exact same problem you've described. Nothing I've tried has worked, but I havn't tried Envy, so I'm in the process of doing that right now. I'll post whether or not it works.

EDIT: Hallelujah!!! : D

---

### Post by ultima on 2008-03-22
This is what worked for me on my Acer AL1916W  monitor and Nvidia GeForce 7300 GS video card.

add the following two lines to your xorg config

```

 Option "ExactModeTimingsDVI"
 Option "ModeValidation" "NoDFPNativeResolutionCheck"

```

at the end of the device section.

For example
```

Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7300 GS]"
        Driver          "nv"
        BusID           "PCI:4:0:0"
        Option "ExactModeTimingsDVI"
        Option "ModeValidation" "NoDFPNativeResolutionCheck"
EndSection

```

and you will also need to add  
```

Modes    "1440x900"

```
to the screen section

for example
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7300 GS]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
        Modes           "1440x900"
        EndSubSection
EndSection

```

save your edited config file then log out

If that works, great. If not continue on.


[COLOR="Red"]**Warning**[/COLOR]: follow the next instructions at your own risk

I had to delete all copies of  my xorg.conf including all backups for this  to work

```

sudo rm /etc/X11/xorg.conf*

```

then run

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

choose the resolution you want, hit the tab button and hit enter.

Tthis should write a new xorg.conf file.

You may need to add the the correct rates to your new xorg.conf

```

HorizSync       30-82
VertRefresh     56-76

```

Now go back and follow the first instructions.

Below is my entire config file

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

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7300 GS]"
        Driver          "nvidia"
        BusID           "PCI:4:0:0"
        Option "ExactModeTimingsDVI"
        Option "ModeValidation" "NoDFPNativeResolutionCheck"

EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     56-76
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7300 GS]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
        Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```

---

