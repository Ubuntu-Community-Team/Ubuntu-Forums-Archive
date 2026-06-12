---
title: "Ongoing TVout issue with svideo &amp; nvidia"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by xpod on 2007-09-13
I had already asked about my problem in [this thread](http://ubuntuforums.org/showthread.php?t=533317&highlight=nvidia+tvout) a couple of weeks ago but i`m using a new card now with even stranger problems.

The initial problem started after attaching [this new monitor](http://www.shopgenie.co.uk/UK_listing/gen/J000165797.html).For 6-7 months our TVout via the svideo to scart had always worked great with an old CRT & the MX4000 i used but upon attaching the new monitor the mouse pointer would no longer move across the screens....I still had the full color desktop on the TV but that mouse pointer was`nt budging.I updated the xorg.conf and even re-installed and started afresh.....all to no avail.

I always had to use [this guide](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition) though as the Twinview/Xinerama options in the Nvidia-Settings utility would never even come close to working.......no matter how i tried

That was two weeks ago and i`ve now replaced the 64Mb MX4000 with a 256Mb FX5500(pci) and this time after trying with Envy on one setup & the restricted drivers manager on another i no longer even get the desktop using the above guide.Then tried swapping driver methods between the feisty/gutsy installs but still no joy.

I can now use the Nvida-settings with this card though but only for the cloned desktops or one big desktop, and only in black & white.I cant get the separate x-screen,not even in black & white.At least the Mouse pointer *does* move across the screens now though.:)
I`ve tried installing NVTV from synaptic but it reckons i dont have a supported card/driver??
I`ve tried numerous variations on the xorg,conf details from similar threads/howto`s but still the same black & white.

I had hoped the new card might solve the original issues of the stubborn mouse pointer  but it`s just swapped for another issue......sod`s law eh:rolleyes:

Relevant xorg.conf sections using mentioned guide but no desktop on TV at all now
```
Section "Device"
	Identifier	"Device[0]"
        Screen 0
	Driver		"nvidia"
	Busid		"PCI:0:10:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
        
EndSection

Section "Device" 
        Driver          "nvidia" 
        Identifier      "Device[1]" 
        Screen 1 
        Option          "TVOutFormat" "SVIDEO" #or Composite etc 
        Option          "TVStandard" "PAL-I" #or NTSC etc 
        Option          "ConnectedMonitor" "Monitor[1]" 
        BusID           "PCI:1:10:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #Primary display
	Option		"DPMS"
        HorizSync        31-83
        VertRefresh      56-75
EndSection

Section "Monitor" 
        Identifier "Monitor[1]" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1400x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1400x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1400x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1400x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1400x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1400x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Screen" 
        Device "Device[1]" 
        Identifier "Screen[1]" 
        Monitor "Monitor[1]" 
        DefaultDepth 24 
        SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
        EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen 0 "Screen[0]"
        Screen 1 "Screen[1]" LeftOf "Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

And this is it if i use Nvidia-settings, but with the black & white results
```

Section "Monitor"
 #Primary display
    Identifier     "Monitor[0]"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
 #TV
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Maxdata (RogenTech) B1925S1W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:0:10:0"
    Screen          0
EndSection

Section "Device"
 #adjust using 'lspci' or cat /proc/pci 
    Identifier     "Device[1]"
    Driver         "nvidia"
    Option         "TVOutFormat" "SVIDEO" #or Composite etc 
    Option         "TVStandard" "PAL-I" #or NTSC etc 
    Option         "ConnectedMonitor" "Monitor[1]"
    BusID          "PCI:1:10:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1400x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1400x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1400x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1400x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1440x900 +0+0, TV: nvidia-auto-select +0+0; CRT: 1280x800 +0+0, TV: nvidia-auto-select +0+0; CRT: 1152x864 +0+0, TV: nvidia-auto-select +0+0; CRT: 1024x768 +0+0, TV: nvidia-auto-select +0+0; CRT: 832x624 +0+0, TV: nvidia-auto-select +0+0; CRT: 800x600 +0+0, TV: nvidia-auto-select +0+0; CRT: 640x480 +0+0, TV: nvidia-auto-select +0+0"
EndSection


```

I know i`m probably beating a dead horse here but if anyone has any suggestions or better ideas i`d be one happy bunny.It`s only for watching movies/slideshows on the TV.We dont actually need the full desktop on the TV,just VLC mainly:)

EDIT:...It`s actually 2 feisty drives & not the gutsy one....my bad

---

### Post by fenian on 2007-09-14
Are you using Beryl or Compiz?

---

### Post by xpod on 2007-09-17
> Are you using Beryl or Compiz?

Thanks for replying but compiz is not the issue i dont think.....dont quote me on that though:)??

We did use the TVout for about 7 months without any real problem but beryls effects would never work on the TV(not that their needed on the TV).
After moving to Compiz-Fusion a couple of months ago though all it`s features did begin working on the TV ,and did so until this new monitor came along.

The TVout always worked great regardless of Composite managers and it was only the day i changed monitors that things went to pot.......first the stubborn mouse pointer....and now with the new card too it`s the black & white TVout  although no seperate X screen.
Compiz still works on the TV though:(

Although it`s a new monitor it only has the VGA output but the FX5500 card has the DVI & VGA outputs so i`m wondering if a DVI to VGA lead for the actual monitor and a VGA to Scart lead for the TVout would make any difference???

We currently use an Svideo to Scart cable and the colors fine on the TV while booting .....until i log in.

---

### Post by farmfield on 2007-09-22
I have exactly the same problem.

I get the TV in colour & everything up until logon, then the TV goes black.

One might think the TV-out isn't working, but I can move my cursor onto the tv-screen  but I get a weird x-like cursor instead of the arrow - and no desktop...

Any suggestions..?

---

### Post by xpod on 2007-09-25
> I have exactly the same problem.

I get the TV in colour & everything up until logon, then the TV goes black.

One might think the TV-out isn't working, but I can move my cursor onto the tv-screen but I get a weird x-like cursor instead of the arrow - and no desktop...

Any suggestions..?

Still in the same boat here unfortunately although i`ve not really had the time to sit banging my head on the walls too much recently:)

I`ve actually went back to encoding stuff for watching via a stand alone DVD player just now.
It`s currently a 5 meter Svideo to Scart lead i use but even after further reading i`m not 100% sure if it`s worth trying other types of cable mabey.Like VGA to Scart possibly.:confused:

It seems it might be possible with the help of some kind of convertor.
[http://www.marimedia.co.uk/erol.html](http://www.marimedia.co.uk/erol.html)

There will be a simple answer eluding me/us somewhere,there always is...
Going back to my old monitor & gfx card is at least one i know of:)

---

### Post by xpod on 2007-10-04
Just to update that we do now have TVout again......eventually.Not with Nvidia though.:)

Swapped some hardware around so that the second machine i have here(the one my younger girls generally use) now has an ATI Radeon 7000(agp) and that seems to be doing the job so far.

It works on the XP drive ok but having just decided to re-install the Ubuntu drive i`m quite surprised to see the TVout working from just the live cd(7.10)....without me doing a thing:)

I had Gutsy on my own second drive for quite a while but even that did`nt have any luck doing TVout with that new nvidia card so this is nice to see.Hope the TVout on the actual install is as painless.

If i`d rummaged through my junk a bit sooner we might not have had the wait we did have to get it running again but there you go.

---

