---
title: "Monitor video messed up after getting tv output working"
date: 2008-07-17
forum: Multimedia Software
---

### Post by chipw on 2008-07-17
I installed a bunch of stuff to get my video output to tv working, and it is working just fine now. Now a problem has developed becuase of something I installed - my monitor video is messed up - it is too short vertically and too long horizontally. My guess is I need to adjust something in the xorg.conf but don't know what, if that is the right place to look. What do you guys think?

---

### Post by markbuntu on 2008-07-17
We could probably help you out but we need some detailed type information, like what video card and driver you have and what you did to it.

---

### Post by chipw on 2008-07-17
heheh, good point. I have a ATI Radeon 9200 AGP vidcard. Following the instructions on this page - [http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout) I installed -

libdrm-dev, mesa-common-dev, x11proto-core-dev, x11proto-fonts-dev, x11proto-gl-dev, x11proto-randr-dev, x11proto-video-dev, x11proto-xext-dev, x11proto-xf86dri-dev, x11proto-xf86misc-dev, x11proto-xinerama-dev,  xserver-xorg-dev, pkg-config.

Then I downloaded and installed xorg7.1-6.6.3-tv_output.patch.gz and xf86-video-ati-6.6.3.tar.bz2

Then I grabbed libxv-dev

The relevant sections of my xorg.conf -

#Section "Device"
#	Identifier	"Configured Video Device"
#EndSection

Section "Device"
    Identifier "Configured Video Device"
    Driver "ati"               
    BusID "PCI:1:0:0" 
    Option "TVOutput" "NTSC"   
EndSection

#Section "Monitor"
#	Identifier	"Configured Monitor"
#EndSection

Section "Monitor" 
    Identifier "Configured Monitor" 
    HorizSync 30 - 50          
    VertRefresh 60 - 60       
    Option "DPMS" 
EndSection

#Section "Screen"
#	Identifier	"Default Screen"
#	Monitor		"Configured Monitor"
#	Device		"Configured Video Device"
#EndSection

Section "Screen" 
    Identifier "Default Screen" 
    Device "Configured Video Device" 
    Monitor "Configured Monitor" 
    DefaultDepth 24             
    SubSection "Display"       
         Depth 24              
         Modes "800x600"       
    EndSubSection              
 EndSection

---

### Post by doas777 on 2008-07-17
hmmm, it looks like your missing the monitor clause for your monitor. the one there is for your TV based on the refresh and synch rates. your problem is likely that your monitor is trying to apply the same settings as yoru TV, which is rather differant in capability.

I usually use differant X screens for each of my heads, so you might want to try that, expecially if you want your monitor resolution differant from the TV res.

hope that helps

---

### Post by doas777 on 2008-07-17
you can check out this xorg (it's nvidia based but should give you some examples) for setting up the TV and monitor as different  X screens.

[http://ubuntuforums.org/showthread.php?t=851626](http://ubuntuforums.org/showthread.php?t=851626)

---

### Post by chipw on 2008-07-17
Thanks guys. Below is my xorg.conf as it is now. What has happened is my monitor shows text so small I need a magnifier to read it, and the tv settings are obviously wrong - my tv is displaying ugly horizontal flashing lines. You can see from the commented out bits what I have tried, but to no avail.

I checked my tv's manual for the refresh info, but it's not there. I checked Sony's web site and the search engine can't find my 10 year old tv. I've searched google for refresh rates and didn't find anything of any help.

What do you think?

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 720 0
    Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Monitor" 
    Identifier "Monitor1" 
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30 - 50
    VertRefresh     60 - 60
#    HorizSync       28.0 - 33.0
#    VertRefresh     43.0 - 72.0
#    Option "DPMS" 
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier "VideoCard0"
    Driver     "ati"
    BusID      "PCI:1:0:0" 
    #Option     "TVOutput" "NTSC"
    Screen     0
EndSection

Section "Device"
    Identifier "VideoCard1"
    Driver     "ati"
    BusID      "PCI:1:0:0" 
    #Option     "TVOutput" "NTSC"
    Screen     1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 800x600 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    #Option         "TVStandard" "NTSC-M"
    #Option         "TVOverScan" "0.0"
    #Option         "TwinView" "0"
    #Option         "metamodes" "TV: 720x480 +0+0"
EndSection

```

---

### Post by doas777 on 2008-07-17
Unfortunately that config was auto-detected for my box, so there are some Nvidia settings mixed in there. 

what I would do is take your original config and adapt it to have the same structure as my example rather than the other way around. whatever configured your xorg probably knows more about your hardware than I do.

I'm in the middle of somthing right now, but I'll try to get back to you tonight.

---

### Post by markbuntu on 2008-07-17
You should look in your Xorg.0.log. It will tell you what it has autodetected for monitor and tv modelines, etc. 

You can then set up your xorg.conf accordingly.

---

### Post by doas777 on 2008-07-17
you can try this:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 800 0
    Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    #HorizSync       30.0 - 82.0
    #VertRefresh     50.0 - 75.0
EndSection

Section "Monitor" 
    Identifier "Monitor1" 
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30 - 50
    VertRefresh     50 - 60
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
EndSection

Section "Device"
    Identifier "VideoCard0"
    Driver     "ati"
    BusID      "PCI:1:0:0" 
    Screen     0
EndSection

Section "Device"
    Identifier "VideoCard1"
    Driver     "ati"
    BusID      "PCI:1:0:0" 
    Screen     1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    SubSection "Display"
	Depth 24
	Modes "800x600"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection "Display"
	Depth 24
	Modes "800x600"
    EndSubSection
EndSection

```

I made a few tweaks, to get you started.  I commented out the monitor vsynch and refresh for the monitor. you will have to do as MarkUbuntu says above to try to get the correct settings for your system. 

hope that helps,

---

### Post by chipw on 2008-07-17
> **markbuntu said:**
> You should look in your Xorg.0.log. It will tell you what it has autodetected for monitor and tv modelines, etc. 

You can then set up your xorg.conf accordingly.

I found the file, it's a mile long and I'm not sure what to look for.

I found this way down in the file -

(**) RADEON(1): RADEONPreInit
(II) RADEON(1): MMIO registers at 0xf9000000: size 64KB
(WW) RADEON(1): Only one monitor detected, Second screen will NOT be created
(**) RADEON(1): RADEONFreeScreen

Those are the only lines referring to RADION(1).

If I run sudo dpkg-reconfigure -phigh xserver-xorg will it create the proper settings for the tv? Providing I run it after a reboot with the s-video cable attached?

At this point my monitor is working fine, but the tv displays a mess of horizontal colored lines flashing, so obviously the info in the .conf is incorrect?

Edit: I rebooted and the tv shows all the boot-up text (bios) and the Ubuntu splash screen, then just before the logon screen appears the tv video goes bonkers.

My current xorg.conf follows -

```

# xorg.conf (X.Org X Window System server configuration file)
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
    Identifier     "Default Layout"
    Screen      0  "Screen0" 800 0
    Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    #HorizSync       30.0 - 82.0
    #VertRefresh     50.0 - 75.0
EndSection

Section "Monitor" 
    Identifier "Monitor1" 
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30 - 81
    VertRefresh     56 - 88
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
EndSection

Section "Device"
    Identifier "VideoCard0"
    Driver     "ati"
    BusID      "PCI:1:0:0" 
    Screen     0
EndSection

Section "Device"
    Identifier "VideoCard1"
    Driver     "ati"
    BusID      "PCI:1:0:0" 
    Screen     1
    Option     "TVFormat" "NTSC-M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    SubSection "Display"
	Depth 24
	Modes "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection "Display"
	Depth 24
	Modes "1024x768"
    EndSubSection
EndSection

```

---

### Post by doas777 on 2008-07-18
your on the right track with the dpkg --reconfigure. 

Once you have the monitor working, adjust your xorg to provide the second Device/Monitor/Screen for your TV. 

I assume your using an analog TV right? are you using composite or SVID?

---

### Post by chipw on 2008-07-18
> **doas777 said:**
> your on the right track with the dpkg --reconfigure. 

Once you have the monitor working, adjust your xorg to provide the second Device/Monitor/Screen for your TV. 

I assume your using an analog TV right? are you using composite or SVID?

The cable is svid with an adapter to convert it on the pc side to rca-jack, plugged into, of course, the yellow video jack. This does work well from my XP box, which I am hoping to replace for most uses.

Edit:
I installed the driver fglrx in hopes that that would solve the video problem, but instead it has caused a major problem - no video at all now. I see the ubuntu splash screen and the logon screen. Then I get a black screen that flashes very quickly. I cannot use alt-ctrl-backspace, I can't switch to another window using the alt-F2 etc keys. I can only do a hard reboot. I tried the second menu option during the bootup menu, got the the terminal, reran the xorg configure script, still no good. It's not a xorg.conf problem now, it has to do with that fglrx driver. How do I uninstall it? I used apt-get to install it. (I'm about ready to just reinstall ubuntu and start all over)

Edit:
I used apt-get remove xorg-driver-flgrx and now when I log into ubuntu the screen goes black with just the X mouse cursor. I've tried a couple different xorg.conf files but they don't seem to have any effect on it.

Edit:
I ran  sudo dpkg-reconfigure xserver-xorg but still no go, just a black screen as above.

---

### Post by chipw on 2008-07-18
Ran this command: dpkg -P --force-depends xserver-xorg && apt-get install xserver-xorg. Still am getting nowhere, just a black screen.

---

