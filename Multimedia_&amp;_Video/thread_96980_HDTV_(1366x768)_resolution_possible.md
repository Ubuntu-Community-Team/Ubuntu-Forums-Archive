---
title: "HDTV (1366x768) resolution possible?"
date: 2005-11-30
forum: Multimedia &amp; Video
---

### Post by kerinin on 2005-11-30
i'm setting up a new system which will be using a samsung LCD tv for its monitor, and i'm curious if there's any way to get it to output video at the aspect ratio that the tv expects.  the TV only takes 1024x768 and 1366x768 input resolutions, so i'd like to use the latter.

i've tried adding it to the screen display values in xorg.conf, but that doesn't work.  is there any way to get around this?

thanks!

---

### Post by kerinin on 2005-12-07
*bump*

i just installed windows on the same system and it allows me to use 1370x768 as my screen resolution, so i'm sure that my card is capable of this...

how can i get ubuntu to do it???

---

### Post by Osamabingandhi on 2006-10-26
Have the same problem, i edit the xorg.conf file to the right resolution but when i restart x that resolution is not there](*,) I think that worked in dapper. Here is my xorg.conf:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	20-82
	VertRefresh	55-90
        #Modeline        "1360x768@60" 84.50 1360 1392 1712 1744 768 783 791 807
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"GeForce 3"
	Monitor		"Generic Monitor"
	DefaultDepth	24

SubSection "Display"
		Depth		24
		Modes		"1280x768" "1366x768"  
	EndSubSection
EndSection

Anyone knows why resolution don't work when i change this?

---

### Post by TheHH on 2006-11-14
Are they working on fixing this issue for the new release?
The only monitor that I use is my HDTV screen and this is the only thing that is not letting me use ubuntu for now.

---

### Post by canardo on 2006-11-30
would also be intrested in how you can do this I tried adding it to xorg but am unable to use it, also on a samsung lcd

---

### Post by Frenchy on 2006-12-08
Ok Guys, I'm here to help.

I have a Samsung 16:9 LCD similar to the ones you have described.  I have it set up successfully on a GeForce 6600 GT and a GeForce 6150.

The issue is that you need to read the Samsung manual.  My manual states clearly (on the last page with all the specs) that it will not work at 1366x768.  It states that the maximum resolution is only **1360x768**.  Check if yours is the same.

When I added this to my xorg.conf it worked immediately, no Modeline. The picture is perfect and there are no stretched pixels like the ones you'll see at 1280x768. 

If you still have no luck then here are some things that have screwed me over when I was trying to set it up:

[LIST=1]
[*]If I use a KVM switch it does not pass the EDID from the screen correctly and won't work.
[*]If I remove the VertSync/HorizRefresh settings that are autodetected from a `dpkg-reconfigure xserver-xorg` then it also fails.  Leave them as the default.
[/LIST]


Hope that helps.

---

### Post by ZarathustraDK on 2007-02-13
Thank you so much for that tip, it works wonderfully now on my Mirai DTL-632V200 (32'').

It's quite an annoying problem since you can modify xorg.conf to your hearts content without it ever having any effect. I got to a point where there where absolutely no mention of any 4:3 resolutions in my xorg.conf, yet the "change resolutions" dialog kept spouting useless 4:3 resolutions at me, which seems counter-intuitive and just plain wrong.

---

### Post by canardo on 2007-03-11
frenchy could you possible post your entire xorg conf file in some code tags, as I cant for the love of me get this to work, even after downloading Samsungs manual and putting in the correct frequencys

---

### Post by grim_d on 2007-04-11
> **Frenchy said:**
> Ok Guys, I'm here to help.
The issue is that you need to read the Samsung manual.  My manual states clearly (on the last page with all the specs) that it will not work at 1366x768.  It states that the maximum resolution is only **1360x768**.  Check if yours is the same.

When I added this to my xorg.conf it worked immediately, no Modeline. The picture is perfect and there are no stretched pixels like the ones you'll see at 1280x768. 


Hope that helps.

how did you manage to do this?

i have added both 1366x768 AND 1360x768 into xorg and i still cannot select either of them through the screen resolution app.

---

### Post by DFragmentor on 2007-04-28
I have added 1360x768 to my xorg conf and it still wont do it. What the hell! How can I tell ubuntu not to look for the EDID. I don't think my tv has a EDID.

I dont have a samsung tv.

---

### Post by DFragmentor on 2007-04-28
I just checked my xprg log and here is what I found.

No valid modes for "1360x768"; removing

what can i do?

---

### Post by luiscon14 on 2007-04-29
> **DFragmentor said:**
> I have added 1360x768 to my xorg conf and it still wont do it. What the hell! How can I tell ubuntu not to look for the EDID. I don't think my tv has a EDID.

I dont have a samsung tv.

Hi... I succesfully connected my HDTV (Sharp AQUOS 32") to my PC by making my own VGA cable. so i didn't connected the EDID pins of the cable. you can use an UTP-5 and buy the VGA plugs on radio shack, the pins used are:
   __________
  /   1  2  3.....\
 /  6  7  8.....   \
/ ...... 13  14 ..\
---------------------

the orientation depends on which side you are looking at the plug. but the pin #s are correct. pins 123 and 678 are for RGB so please use a pair of cables (for example, Orange 1, White-Orange 6) that's for the red, then 2 and 7 for the green and 3 and 8 for the blue (use green and blue pairs for those)....13 and 14 can be connected with brown pair,  this carry the H and V sync signals.... just check that both sides of the cable are identical and thats it, you have a VGA cable that does not send EDID.

also... if your tv has a DVI input (as mine) you must enter in the menu that it should receive Analog video, cause VGA is analog and DVI is digital. but my TV supports both. BUT when i use the DVI cable the TV tells the video card that it doesn't support 1360x768... its weird and bad but.. what can we do?.

our own VGA cable with no EDID pins !!!

good luck.

By the way... my tv also supports only 1360x768 (the tv setup menu asks for the expected input resolution and it only have 2 options, 1360x768 and 1024x768, obviously you want 1360),,, its not an edid problem, i think video cards just have bloked that resolution (1366), but it looks really great at 1360. 

DONT select auto-adjust or fit the image to the screen, that will make unaccurate pixels. because the tv WILL stretch the 1360 signal to 1366 pixels (Total resolution of the LCD panel), Sharp Aquos has an option of "pixel per pixel", that shows a perfect image, each pixel received is one pixel of the display. the 6 remaining are black pixels (3 on each side) but it doesn't bother, you wont even notice them.

there are other brands that my not have this options... 

Luis Conrado

---

### Post by Elandar on 2007-05-13
hi,

any (software)solution out there yet?

my xorg.conf 
```

Section "Device"
	Identifier	"Generic Video Card-1"
	Driver		"nvidia"
	Busid		"PCI:6:0:0"
	Screen		1
	#Option		"AddARGBVisuals"	"True"
	#Option		"AddARGBGLXVisuals"	"True"
	#Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"loewe"
	Device		"Generic Video Card-1"
	Monitor		"HDTV"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1366x768"			
	EndSubSection
EndSection
```
produces
```
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce 7950 GT at PCI:6:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 05.71.22.42.06
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 7950 GT at PCI:6:0:0:
(--) NVIDIA(1):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(1):     LOEWE HDMI TV (DFP-1)
(--) NVIDIA(1): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(1): LOEWE HDMI TV (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): LOEWE HDMI TV (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(1): Assigned Display Device: DFP-1
(WW) NVIDIA(1): No valid modes for "1366x768"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 1280 x 720
(++) NVIDIA(1): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
```

and I'm pretty sure 1366x768 is the right solution (I have the tv-manual right next to me) :-)

---

### Post by pijiu on 2007-05-13
I had the same problem untill I rebooted my laptop then the resolutions became available.

p.s. it should be 1360x768 not 1366.

---

### Post by williammanda on 2007-05-14
Please use the following:
Option "UseEDID" "True" 

DefaultDepth 24 
SubSection "Display" 
Depth 24 
Modes "nvidia-auto-select" 
EndSubSection 

Refer to the example below

Section "Monitor" 
Identifier "SONY TV" 
#HorizSync 15.0 - 46.0 
#VertRefresh 59.0 - 61.0 
Option "DPMS" 
**Option "UseEDID" "True" **
EndSection 

Section "Device" 
Identifier "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]" 
Driver "nvidia" 
EndSection 

Section "Screen" 
Identifier "Default Screen" 
Device "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]" 
Monitor "SONY TV" 
#Option "FlatPanelProperties" "scaling = centered" 
DefaultDepth 24 
[B]SubSection "Display" 
Depth 24 
Modes "nvidia-auto-select" 
EndSubSection [/B]
EndSection 

This will allow xorg.conf to read your monitors spec's and apply them accordingly. My monitors resolution is 1366*768 but I can only get 1360*765. I can't tell the difference.
Thanks

---

### Post by tseliot on 2007-05-14
kerinin :
can you post the model of your card?

---

### Post by Elandar on 2007-05-14
I'm using a GeForce 7950.
As monitor a SyncMaster 930BF (works perfectly)
and as sec. screen I'd like to use my HDTV (a Spheros R26 - connected over a DVI-HDMI-cable)

I tried the "UseEDID" Option:
```
(--) NVIDIA(1): LOEWE HDMI TV (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): LOEWE HDMI TV (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(1): Assigned Display Device: DFP-1
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     **"nvidia-auto-select"**
(II) NVIDIA(1): **Virtual screen size determined to be 1280 x 720**
(++) NVIDIA(1): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(from the Xorg.0.log)
```

which is kinda funny, because after reading this:
> A major limitation of EDID is that it cannot express the native resolutions of the most common wide screen flat panel displays and liquid crystal display televisions. The number of horizontal pixels must be a multiple of 8. The number of vertical pixels is calculated from the horizontal resolution and the selected aspect ratio. To be fully expressible, the size of wide screen display must thus be a multiple of 16×9 pixels. For 1366×768 pixel Wide XGA panels the nearest resolution expressible in the EDID syntax is 1360×765 pixels. Specifying 1368 pixels as the screen width would yield an unnatural screen height of 769.5 pixels.

Many Wide XGA panels do not advertise their native resolution, instead offering **only a resolution of 1280×768.** Some panels advertise a resolution only slightly smaller than the native, such as 1360×765. For these panels to be able to show a pixel perfect image, the **EDID data must be ignored** by the display driver. Special programs are available to override the EDID data; PowerStrip for Microsoft Windows and DisplayConfigX for Mac OS X

[http://en.wikipedia.org/wiki/EDID](http://en.wikipedia.org/wiki/EDID)


I'm suspecting EDID running properly might be the problem :lolflag: 

sadly there isn't listed a program to override the EDID data for Linux... 
does any one of you, know one?  respectively a nice hack?

---

### Post by shill88 on 2007-05-16
Is there anyway of doing what they are doing in this post with an ATI or nVidia card? [http://ubuntuforums.org/showthread.php?t=203905](http://ubuntuforums.org/showthread.php?t=203905)

Thanks

Shawn

---

### Post by williammanda on 2007-05-16
I f EDID is the problem then several people I know and including myself would be having problems. I disagree with the statement that you referenced. One other possibility would be to put 1360*765 in the mode along with using the EDID option.

Section "Screen" 
Identifier "Default Screen" 
Device "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]" 
Monitor "SONY TV" 
#Option "FlatPanelProperties" "scaling = centered" 
DefaultDepth 24 
[B]SubSection "Display" 
Depth 24 
Modes "nvidia-auto-select" 
EndSubSection 
SubSection "Display" 
Depth 24 
Modes "1360x765" 
EndSubSection [/B]
EndSection 

I remember that I had to do this for one version of debian. Also the first example of using EDID and nvidia-auto-select was taken from a user that just got it to work. They saw it on my post in another forum.
Thanks

---

### Post by williammanda on 2007-05-16
Another possibility would be to run the nvidia software, nvidia-settings (from the console), and setup the resolution for 1360*765. Select the button to save the change to your xorg.conf file (which you should be able to view the changes before saving) but don't actually save it. Copy and paste that info here and we could use that infomation to update your xorg.conf.
Thanks

---

### Post by Elandar on 2007-05-18
hi, 

> SubSection "Display"
Depth 24
Modes "nvidia-auto-select"
EndSubSection
SubSection "Display"
Depth 24
Modes "1360x765"
EndSubSection 
didn't work

> setup the resolution for 1360*765
1360*765 isn't in the menu, from which I have to chose from. 1280x720 and 800x600 are the nearest/highest ones

for 1280x720 the xorg.conf File would look like that:
```

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LOEWE HDMI TV"
    HorizSync       28.0 - 48.0
    VertRefresh     48.0 - 62.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GT"
    BusID          "PCI:6:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "DFP-1: 1280x720 +0+0; DFP-1: nvidia-auto-select +0+0; DFP-1: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by ufgrat on 2007-10-07
> **williammanda said:**
> I f EDID is the problem then several people I know and including myself would be having problems. I disagree with the statement that you referenced. One other possibility would be to put 1360*765 in the mode along with using the EDID option.


I don't normally resurrect ancient threads, but since I don't see anyone with the solution I used, I'll post my personal experience here in case it helps someone.

I have a Polaroid FLM-3232 LCD TV, which has been a nice TV, except that the EDID modes it outputs do not include 1360x768 or anything close.  You can see what is output by going through the /var/log/Xorg.0.log file.  In my case, it was declaring 1280x768 as it's best mode, and the binary NVidia driver _insisted _on using EDID.

I had to disable EDID, then specify the valid modeline.

```
Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "ModeValidation" "NoEdidModes"
EndSection

Section "Monitor"
        Identifier      "FLM-3232"
        Option          "DPMS"
        Modeline      "1360x768" 84.06 1360 1392 1712 1740 768 771 777 806 -HSync -VSync
EndSection

```

I believe I used xvidtune to generate the modeline, but that's not in my documentation.

Hope that helps someone.

---

### Post by chekza on 2007-10-07
Hey guys extremly new person here. hah

Im hoping someone can help me out here.
It would seem im having the same problems as the rest of the other people in this thread.
Im also trying to run a resolution of 1360x7698, now I am coming from windows and have had it run at the res more almost a yr with no problems at all so i know I can use it with this tv. Basicly I was wondering if someone would be ever so kindly give me a fool proof way of changing the res.
Ive tryed the other way sugested in other threads but alas they have failed.
What I am running atm. 
Tv : Teac 32" Lcd 3233a
Grafx: Ati radeon 9550pro
Via VGA inputs.

I have enabled restricted driver manager and the ati driver but still nothing.

So hope someone can help, do really like Ubuntu atm would hate to go back to windows hah.

---

### Post by phidia on 2007-10-16
The use of LCD TV's as monitors hasn't been fully realized in linux yet or so it seems.
I have read several threads here and at other forums but getting 1366 (or 1360)x768 screen rez is not been possible for me.
I will try what ufgrat listed in post #22 and report back. I think I already tried that but I'll redo the xorg.conf once again. 
I think we need a sticky thread on LCD TV monitors-a place for people to list models that work and the methods they use.

Afterwards: No I cannot get 1360/1366x765/768 resolutions. The most usable rez possible for me is 1280x720 using hdmi/dvi cable.
The top & bottom panels are mostly off screen but I can manage to figure out where things are. I might try installing gutsy on another partition to see if that's any better. BTW this system i'm doing this with is not my normal desktop just and older computer I've used for movies and stuff. I really wish I could get 136*x76* rez.

---

### Post by Youkai on 2007-11-11
I agree that the support for non-standard display devices is very poor in LInux, and I have no general answers.  But I thought I'd post my success story, for others who may be able to use it.

My equipment:
  PC: A laptop (Compaq Evo N610c) with built-in ATI Radeon (Mobiility 7000?), and DVI-D and VGA outputs.
  OS: XUbuntu 7.04 (Feisty Fawn).
  TV: Sharp Aquos LC374G

What the solution ended up looking like:
  PC displaying on the TV, at native 1366x768 resolution, via the VGA output.  The laptop's own LCD display is completely disabled (which is OK for me, since the laptop is a dedicated media PC, and I don't actually want the second display active)

The story on how I got the solution to work:

By default, my laptop & ubuntu would mirror the display on both the laptop panel, and the TV, at an 1024x768 or 800x600 resolution.  The display settings applications were useless, because the system was not able to detect the actual supported resolution of the TV.  So that meant having to edit the xorg.conf file manualy.

I struggled to get the DVI output working, using all kinds of options documented in the radeon driver man page, but was never successful.  I also tried for a while to get the the laptop display and the tv working as a dual display, but didn't get that to work either - it always catered to the laptop panel, ignoring the settings for the TV.

Eventually, I figured out how to disable the onboard display, and get the driver to focus solely on the external VGA port.

Also, I switched from KDE to Gnome/X, because even after I got it working, whenever I rebooted, something in KDE would reset the resolution.

Here are the relevant portions of my working xorg.conf.  The comments marked with '#' are the changes I made:

```
Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Driver          "ati"
        BusID           "PCI:1:0:0"

        # disables the laptop panel
        Option "MonitorLayout" "CRT,NONE"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"

        # Must override the sync/refresh ranges reported by the TV,
        # otherwise the modeline below will be ignored.
        HorizSync 40-80
        VertRefresh 50-80

        # DVD/video playback apps need this, to play videos in the proper aspect ratio
        DisplaySize 8192 4636

        # custom modeline computed using the 'gtf' command
        # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
        Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Monitor         "Generic Monitor"
        DefaultDepth    24

        # Use the one-and-only-one resolution that we configured above
        SubSection "Display"
                Depth          24
                Modes          "1368x768_60.00"
        EndSubSection
EndSection

```

Prologue: I upgraded to Gutsy Gibbon last night, and it no longer works, even with exactly the same xorg.conf file.  The DVI port works now, but it just mirrors what's displayed on the laptop display, and at a low resolution.

So I'm back at square one.  I'm a glutton for punishment, and Linux has plenty to dish out.

-Chris Thomas

---

### Post by BrandonMintern on 2007-11-20
Note that if your widescreen is reporting bogus resolutions, it may be necessary to add the following to your Device section for nvidia:

Option "ModeValidation" "NoWidthAlignmentCheck, NoDFPNativeResolutionCheck"

Disabling the first check allows resolution widths which are not divisible by 8, and the disabling the second check sends the signal to your monitor even though it claims that it cannot display it. I had to do the second even while I had "UseEDID" "false" specified.

---

### Post by alphane on 2007-11-23
Hi guys,

Been lurking a while trying to get some widescreen action going on my Mirai 27" LCD HDTV.
I've been watching this, and a few other threads, whilst spending the last 3 hours dropping to TTY2 to update xorg.conf then restarting X to see the improvements.

I FINALLY got what I wanted 1360x760 usplash, and 1360x768 desktop, after a LOT of playing around, breaking, commenting out, et al.  At one point I invoked either bullet proof x or some gnome failsafe, that then re-wrote my xorg.conf (hence the way it looks) but it was actually one of the last steps to getting where I needed to be!

I've posted my xorg.conf and usplash.conf so that those that are better than I may be able to glean some information from it.  I understand that my xorg.conf is EXTREMELY messy, and I need to spend some time cleaning up commented lines, and perhaps understanding what is actually doing what, but not for the moment, for now, yes, I think I'll just enjoy a bit of widescreen lovelyness...

XORG.CONF
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  #modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  #modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1360x768@60" 84.72 1360 1424 1568 1776 768 769 772 795 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	16
	SubSection "Display"
		Depth	16
		#Virtual	1024	768
		Modes		"1360x768@60"
#	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	16
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

USPLASH.CONF
```
# Usplash configuration file
xres=1360
yres=768

```

I seriously hope that this will point someone in the right direction after fighting to get even 1024x768 in anything but a refresh of 85hz... good night all!

---

### Post by aMadMan on 2007-12-08
Greetings everyone.

(NOTE: I am using an nvidia card in the PC that i worked the below issues out with, i am also using the nvidia driver.  I am not sure if this applies to ATI cards or not.  before messing with your xorg.conf file, BACK IT UP.  know how to restore it should any of your changes mess it.  proceed at your own risk.)

I've been watching this thread for a while trying to get widescreen resolutions to work with ubuntu for a few weeks now.  I just got it working today and figured i would share what made it work for me.  Since it is not reccomended to just copy other ppls xorg.conf file I will elaborate on what steps i took.

First things first, you need to know what resolution your HDTV is capable of, this thread mentiones 1368x768. (but this should apply to basically any resolution)  you also need to know the refresh rate.  for my TV it's 60

The next thing we need now that we know the above information, its the "modeline" that we want to use.  use gtf to get that. (comes installed on ubuntu)

Use the resolution and refresh rate that you figured out above, in my case i would run   in a terminal:

```
gtf 1368 768 60
```

What you will get is something like this:

```
# 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```

Copy the output of the gtf command and put it in the "Monitor" section of your xorg.conf.  This is what mine looks like:

```
Section "Monitor"
	Identifier	"Q9-2 Series"
	Option		"DPMS"
	# 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
        Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
EndSection
```

(the above is for reference only, your monitor section may look different)

Now that we have that done, let's setup the "Device" section.  I had to add the following two lines to the end of mine to make it work for me:

```
Option "UseEDID" "False"
Option "ModeValidation" "NoEdidModes, NoMaxPClkCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoEdidMaxPClkCheck"
```

This is what mine ended up looking like after I modified it:

```
Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"UseEDID"	"False"
	Option 		"ModeValidation" "NoEdidModes, NoMaxPClkCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoEdidMaxPClkCheck"
EndSection
```

(the above is for reference only, your device section may look different)

The first one we added, "UseEDID" is set to false so that the bogus resolution data your HDTV sends is ignored.  The second part was what made all this work for me, before i added it, xorg reported in /var/log/xorg.0.log that my newly added modeline was invalid.  But after i added that, all was cherry.

Last but not least, there is the "Screen" section.  Here is what mine looked like BEFORE i modified it:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Q9-2 Series"
	Defaultdepth	24
	SubSection "Display"
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

This is what it looked like AFTER:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Q9-2 Series"
	Defaultdepth	24
	SubSection "Display"
        Modes "1366x768_60.00" "640x480"
        #Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

As you can see, i commented out the oringal "Modes" item and added my own that only shows the custom modeline we created above, as well as the basic 640x480.

After that, save your xOrg.conf, make sure you have a backup and then restart X or reboot your PC.  remenber to be prepared to switch to a text only prompt if for some reason X does not come up.  restore your xorg.conf backup, then check /var/log/xorg.0.log for any errors.  reboot or restart X and then try to figure out whats up.  However, what i did above made it all work for me.

Good luck!

---

### Post by Crowie on 2007-12-30
Has anyone managed to get 1366x768 working using sis graphics driver.

Im currently using latest mythbuntu on gutsy and can only get 1024x768.  xorg log reports that its not vesa standard and defaults to the next available vesa standard being 1024x768.
I know my TV can support 1366x768 xresprobe reports

id: 37V1A-A6A
res: 1366x768 1280x1024 1024x768 832x624 800x600 720x400 640x480
freq: 24-60 50-85
disptype: 

and ddcrobe repotrs

vbe: VESA 3.0 detected.
oem: SiS
vendor: Silicon Integrated Systems Corp.
product: 6325 1.14.07
memory: 65472kb
mode: 800x600x16
mode: 640x480x256
mode: 640x400x256
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 320x200x32k
mode: 320x200x64k
mode: 640x480x32k
mode: 640x480x64k
mode: 800x600x32k
mode: 800x600x64k
mode: 1024x768x32k
mode: 1024x768x64k
edid: 
edid: 1 3
id: 4c54
eisa: YHI4c54

I see with nvidia there is an option to ignore edid etc.  Is there an option to overide this for sis and allow non-vesa standard 1366x768 to be used.

Ive tried sisctrl also from gui but it doesnt even display option for 1366x768.

TIA

---

### Post by aMadMan on 2008-01-02
Re: SiS,

I did not have much luck finding any sort of "No EDID" flag for the SiS driver but did see a few threads that discuss what looks to be a possible workaround.. (can't try it myself as i dont have an SiS card)

[http://g-ding.tv/?q=node/2555](http://g-ding.tv/?q=node/2555)

[http://www.mythtv.org/wiki/index.php/Display_Size](http://www.mythtv.org/wiki/index.php/Display_Size)

Probably not the silver bullet answer but might help point you in a direction to try some things at least.

~S

---

### Post by Crowie on 2008-01-04
not much success there, my tv is displaying 100x100DPI and mythtv is displayed fine.
It seems to be that the sis driver searches for the available vesa standards and uses those.  Unfortunately the next one in the list is 1024x768.
none of the modelines ive added into xorg.conf are accepted.
Im using a pundit with two dvb cards in the 2 pci slots available so unable to use one for an nvidia card. doh! will keep googling for an answer

---

### Post by kidcharles on 2008-02-22
Ugh, I've tried everything in this thread, to no avail. My problem is I have a Sharp Aquos 32" LCD TV. It has a single VGA input and 2 HDMI inputs. I can display a proper 1360x768 resolution with no problems if I use the VGA input, sometimes I need to do an autosync but not a big deal. I have a new video card that has a DVI out that I want to connect to one of the HDMI inputs. It works but there is an obnoxious problem where a little bit of every side of the desktop is not visible, which of course includes the all-important panels. It demands to use 1280x720 if I use the nvidia driver, if I use the 'nv' driver it allows me to run at 1360x768 at 60 Hz but the problem where not all of the screen is displayed remains. I have another machine using the VGA output, I want to use the HDMI input for the new one. Any advice? Anyone still checking in on this thread?

---

### Post by jelofson on 2008-03-05
> **kidcharles said:**
> Ugh, I've tried everything in this thread, to no avail. My problem is I have a Sharp Aquos 32" LCD TV. It has a single VGA input and 2 HDMI inputs. I can display a proper 1360x768 resolution with no problems if I use the VGA input, sometimes I need to do an autosync but not a big deal. I have a new video card that has a DVI out that I want to connect to one of the HDMI inputs. It works but there is an obnoxious problem where a little bit of every side of the desktop is not visible, which of course includes the all-important panels. It demands to use 1280x720 if I use the nvidia driver, if I use the 'nv' driver it allows me to run at 1360x768 at 60 Hz but the problem where not all of the screen is displayed remains. I have another machine using the VGA output, I want to use the HDMI input for the new one. Any advice? Anyone still checking in on this thread?

Ditto. I have an Aquos 37" and I get the very same problem as you. Using DVI->HDMI I can't get any better than 1280x720 and the outer edge is missing. I haven't actually tried the nv driver. 

I did try adding the modeline from gtf and setting the modes as per one of the other posts, but my Xorg.0.log complains that that mode isn't valid. Not sure what I was doing wrong. I don't know why I can select a 1360x768 LCD in the list of displays, but can't select that resolution. Arggg. I can post my xorg.conf if it's at all useful. I have used the nvidia-settings utility but it pretty much does the same stuff. Adds metamodes to the xorg.conf file.

Jon

---

### Post by Gisli Ottarsson on 2008-04-13
Jelofson and Kidcharles:

I have to pipe in with a me-too.  Me experience is just like yours, albeit with a 42" Aquos.

Like you, I have had decent success with the vga inputs (EXT4 on my TV set), although the 1360x768 mode gave me some flicker which caused me to gravitate toward the less noisy 1280x720 mode.  I've attributed the noise to the DVI to VGA adapter I had to use on my DVI-only videocard. (nVidia Corporation G70 [GeForce 7600 GT] rev 161)

The DVI to HDMI seemed like it would be the ideal, but I have had a rotten time getting it to work. (I use EXT5 on my set) and use analog audio inputs.  Note that I would be totally content with a solid 1280x720 mode, but, like you, I am currently missing several pixels from each edge of the display.  Using the TV settings I can pan the display up/down and left/right, just enough to be able to see half the top and bottom panels (GNOME).  I also seem to be having some compiz issues so I have had to turn off 3D effects.

My experimentation has been mostly limited to the NVIDIA proprietary driver.  Here is what I think I have discovered:

If I do not supply any modes, nvidia-auto-select kicks in with a 1280x768 mode (actually it refers to a virtual screen but never specifies a resolution).  If I specify a virtual screen, like this, 

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
       Virtual     1280 720
       Depth       24
    EndSubSection
EndSection

then I can get the 1280x720.  This seems to make a difference to whether I can see the bottom panel.

I have several modelines which I considered promising:

  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline "1280x768" 80.14 1280 1344 1480 1680 768 769 772 795                
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync         
  modeline  "1368x768" 85.5 1360 1424 1536 1792 768 771 776 794 -hsync -vsync                                                                           
  modeline "1360x768" 85.800 1360 1400 1534 1800 768 771 781 794         
  modeline "1360x768@59" 82.78 1360 1392 1704 1736 768 783 791 807   

but all are rejected.

I've noticed that the TV flashes "720p, 60Hz" which has made me wonder whether the mode needs to be exactly 60Hz but I have not followed up on that hunch.

I experimented with suppressing the EDID, e.g. with:

Option "UseEdid" "FALSE"

but it seems that if you do this, the NVIDIA driver wimps out and limits the resolution to 800x600 (as a precautionary measure, it would seem).  If no modeline of 800x600 or smaller is provided, then you get a blank screen.

I tried all manner of other options in order to sneak a modeline past the mode checking algorithms, e.g. 

#    Option "UseEDIDFreqs" "FALSE"                                              
#    Option "UseEDIDDpi" "FALSE"  
    Option "ModeValidation" "NoMaxPClkCheck, AllowNon60HzDFPModes, NoVesaModes,\
 NoDFPNativeResolutionCheck"#,NoEdidModes" 

I would get many different results, ranging from a blank screen to a rejection of all modes and falling back on that lame 1280x720 mode, to an apparent acceptance of the mode but with a distorted screen.

Note that I found that the best way to experiment is to remotely log in to the machine, edit xorg.conf from a terminal and 'sudo /etc/init.d/gdm restart' to try my changes.

I am using Ubuntu 7.10

Any ideas?  

  Gisli

PS:  I came across this article which raised a lot of questions for me.
[http://hd1080i.blogspot.com/2006/12/1080i-on-1366x768-resolution-problems.html](http://hd1080i.blogspot.com/2006/12/1080i-on-1366x768-resolution-problems.html)

---

### Post by Trollslayer on 2008-04-16
Use 1280 x 720, the rest is for overscan.

---

### Post by jelofson on 2008-04-24
That makes sense. When I get home, I am going to check for any overscan settings with the nvidia-settings, my TV, and if they don't pan out, I am going to dig into the modelines. I found this pretty interesting:
[http://mythtv.org/wiki/index.php/Working_with_Modelines](http://mythtv.org/wiki/index.php/Working_with_Modelines) (see near the bottom where it talks about getting rid of overscan).
Who knows, it might work :)

---

### Post by kidcharles on 2008-04-26
Success!

I just did a fresh install of the new 8.04 release (64-bit version). I installed the nvidia-new package, but the max resolution it wanted was 1280x768. All I did to fix this was to add the following "Display" subsection to the "Screen" section in my /etc/X11/xorg.conf file.

```

Subsection "Display"
    Depth    24
    Modes    "1360x768"
EndSubSection

```

Now I get a perfect display on my Sharp Aquos 32" LCD, no missing pixels on the edges. I imagine the new nvidia drivers may have fixed the previous bug, but I really don't know why it is working now and didn't before. Here is the entirety of the relevant sections in the xorg.conf file (the original file had no "Display" subsection):

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes   "1360x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

---

### Post by feenicks on 2008-07-01
YES!

I finally have a perfect widescreen resolution of 1360x768, thanks to aMadMan in post #28.  THANK YOU!!!

---

### Post by Fen_Star on 2008-07-11
I was able to get a custom resolution (1360x768) as a choice for display size, but nvidia was scaling it to what it thought the screen size was from the EDIE. Is there a way to tell it to not scale? I unchecked Force full GPU scaling, but that didn't do anything.

---

### Post by Fen_Star on 2008-07-14
I finally got a resolution of 1366x786 by editing the EDID.

This thread was a big help:
[http://softwarecommunity.intel.com/isn/Community/en-US/forums/1/30238789/ShowThread.aspx](http://softwarecommunity.intel.com/isn/Community/en-US/forums/1/30238789/ShowThread.aspx)

After spending countless hours on this, I would be happy to try to help anyone who is trying to get 1366x786 over DVI/HDMI.

---

### Post by Kileli on 2008-07-14
ok im in a little trouble here. as you probably can tell i am new to linux and got a little carried away editing the xorg.conf file. now my resolution is all jacked up i cannot obtain a resolition higher than 680* on my monitor. i was attempting to fix the resolution on my RCA HDTV and have done a number on myself. oh and i forgot to make a back up of my file(not something i will be doing again anytime soon) can sombody please post the entire code of  their xorg.conf file so i can compare?

---

### Post by Jean__ on 2008-07-15
To those people having overscan, I have an option on my tv called 'scan only' for a certain input and I got rid of all overscan problems. I only figured that out later after searching and fiddling with mplayer options and the like.
I'm sorry if this does not help.

---

### Post by danb0087 on 2008-07-18
To get 1366x768, I removed all resolutions/modelines from xorg.conf and added:
Modes "1280x768"
to the Display subsection

This, for whatever reason, displays 1366x768 on my hdtv (primary).
Hardy, ATI 9800 Pro - Catalyst 8.6 proprietary driver (fglrx)

---

