---
title: "Fixing overscan on TV"
date: 2010-02-15
forum: Mythbuntu
---

### Post by IceCap on 2010-02-15
My Mythbuntu setup includes a Nvidia 7600GS hooked up to a 1080i CRT (Samsung TXM2927HX) through the component connection.

  I have been running it in 640x480 mode and now I'm trying to tame the 1080i mode.  Currently my xorg.conf looks like this

```
Section "Device"
	Identifier	"Gigabyte NVidia 7600 GS"
	Driver		"nvidia"
	Vendorname	"nVidia Corporation"
	Boardname	"GeForce 7600GS"
	BusID 		"PCI:1:0:0"
	Option		"AddARGBGLXVisuals" "True"
	Option 		"NoLogo" "True"
	Option		"RenderAccel" "1"
   	#Option		"NvAGP" "2"  # 0: disable AGP 1:	use NVIDIA's internal AGP support, if possible  2: use AGPGART, if possible  3: use any AGP support (try AGPGART, then NVIDIA's AGP)
	Option   		"UseEvents" "True"
	Option		"DynamicTwinView" "false"
EndSection

Section "Monitor"
	Identifier	"SamsungTV"
	HorizSync	30-50
 	VertRefresh	45-61
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Gigabyte NVidia 7600 GS"
	Monitor		"SamsungTV"
	DefaultDepth	24
	Option		"UseEDID" "FALSE"
	Option 		"TVStandard" "HD1080i"
	#Option		"TVStandard" HD480p"
	Option		"ConnectedMonitor" "TV"
	SubSection "Display"
		#Viewport 0 0	#Do we need this?  If not the initial display will be centered on the virtual display
		Depth 24
		Modes "1920x1080" "1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x576" "720x400" "640x480"
	EndSubSection
EndSection
```

  I have two issues.  First, I have a large overscan.  OK not a huge problem for MythTV since I can scale it back using the Wizard, but I'd like to fix this.  So I found this thread [here]("http://www.gossamer-threads.com/lists/mythtv/users/324261") where he recommends using custom modelines in xorg.conf.  Namely something like:

```
Mode "my1080i" 
	DotClock 74.52 
	HTimings 1640 1888 2096 2208 
	VTimings 952 1044 1060 1126 
	Flags "-HSync" "-VSync" "Interlace" 
EndMode 
```

  I get the whole logic around this but how do I integrate this this into my xorg.conf (do I take something out, does this just come at the bottom)?  I'm assuming that I can add multiple of these in xorg.conf (with different names and different offsett/size) and then try them out in the monitor settings?

  Secondly, what happened to the resetting the MythTV offsett/size in the Wizard?  I can't find it.  When I run using the 1080i mode, MythTV and MythWelcome are still 640x480 pixels in the corner.  I'm assuming I need to reset the Wizard scaling but I can't find it (running Mythbuntu 9.10).

  Thanks

   IC

---

### Post by Grenage on 2010-02-15
While I have don't have experience with myth, but modelines generally go in the *monitor* section, albeit in a different format - but it's the same info:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "DCLLCD"
	ModelName "DCL20AT"
	HorizSync 24 - 82
	VertRefresh 50 - 75
Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
EndSection
```

---

### Post by IceCap on 2010-02-15
That's how I have seen the Modelines.  Can I put multiple of these in a row and then switch between them using the system Display settings to check out which one works the best?

  Thanks

  IC

---

### Post by IceCap on 2010-02-15
Actually, I have a slightly different question regarding fixing the overscan issue.

  So my understanding is that the nvidia utility does a nice job of fixing the overscan.  My problem is that when I switch to 1080i resolution, the font becomes so small I can't read much on the desktop (mythtv is fine).  What I have been doing is to "ssh -X" into the mythtv box from my Mac Mini which (by starting the X environment) allows me to run GUI programs on the mythtv box but they show up on the Mac.
  But when I run the nvidia utility it applies to the Mac screen and it doesn't recognize it (besides, it needs to be applying any changes to the TV not my Mac screen.

  Anyway I can go around this?

  Thanks

  IC

---

### Post by Lepy on 2010-02-16
Something I posted in another thread, works best if you do all of this via ssh from another machine.
Find your TV's optimal resolution from the manual or online (eg 1366X768@60)
Issue the gtf command:
```
gtf 1366 768 60

  # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```

In your xorg.conf, under your monitor section add the gtf modeline output

        ```
Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Proview"
        ModelName      "Unknown"
        HorizSync       31.0 - 80.0
        VertRefresh     56.0 - 75.0
        Option         "DPMS"
        Option         "ExactModeTimingsDVI" "True"
        Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync


```
and under the screen section add the modeline reference (using only one "Modes" until you find a few that are appropriate, works best)

        ```
SubSection "Display"
                Depth       24
                Modes   "1368x768_60.00"
        EndSubSection
```

Next issue "/etc/init.d/gdm restart" and hope the overscan is fixed. If it is not a compatible resolution, the screen won't show anything (out of range or something). This is why using ssh is the best approach.

If that "gtf" does not work, you may need to try a different "gtf" depending on your tv resolution. My monitor (1366x768) had an optimal resolution using "gtf 1344 770 60" so don't be afraid to tweak the gtf until you get something that fixes the overscan.

---

### Post by TheMiz on 2010-02-16
> **IceCap said:**
> Actually, I have a slightly different question regarding fixing the overscan issue.

  So my understanding is that the nvidia utility does a nice job of fixing the overscan.  My problem is that when I switch to 1080i resolution, the font becomes so small I can't read much on the desktop (mythtv is fine).  What I have been doing is to "ssh -X" into the mythtv box from my Mac Mini which (by starting the X environment) allows me to run GUI programs on the mythtv box but they show up on the Mac.
  But when I run the nvidia utility it applies to the Mac screen and it doesn't recognize it (besides, it needs to be applying any changes to the TV not my Mac screen.

  Anyway I can go around this?

  Thanks

  IC
  

I the problem with the fonts, and this post: [http://ubuntuforums.org/showthread.php?t=1364974](http://ubuntuforums.org/showthread.php?t=1364974) fixed it.

---

### Post by IceCap on 2010-02-28
First of all, thanks TheMiz, such a simple solution and why I didn't think of that I'll never know.

  Anyway, now that I can start playing around while still using the 1920x1080 resolution I started playing with modelines, per Lepy's suggestions.

  So several observations.  If I let nvidia-settings auto detect the resolution it picks 1028x768 so I'm wondering if this is the maximum resolution (the 1920x1080 looks pretty bad, lot of flickering in normal desktop, Mythtv looks OK).  But when I let the utility write its version of xorg.conf (actually it looks like when I comment out the HD1080i option in my version of xorg.conf and put in a modeline this happens) the white turns blue-ish on the screen.  The 1024x768 actually looks pretty good (no flickering and no overscan, both fixed by the nvidia-utility I assume) but it is blue.  I'm assuming that this is some sort of a sync issue that needs to be manually corrected (maybe 60Hz isn't the right frequency).

  Also, when I use my xorg.conf listed above, I don't get the option to fix overscan in the nvidia-settings utility.  Several items on that page don't show up.  Maybe that is an indication that I'm not running in a real 1080 mode (the TV claims 1080i on the front though).

  Any help/insight/information would be appreciated.

  Thanks

  IceCap

---

### Post by nickrout on 2010-02-28
Have you tried changing the overscan in the nvidia-settings gui program? You need a recent driver version and a recent copy of nvidia-settings.

---

### Post by IceCap on 2010-02-28
> **nickrout said:**
> Have you tried changing the overscan in the nvidia-settings gui program? You need a recent driver version and a recent copy of nvidia-settings.

  Well, when using the supposedly 1080i setup (by using ```
Option 		"TVStandard" "HD1080i"
``` I don't get the option to fix the overscan in the nvidia-settings gui program.  The page is missing most of the tools.  When I ran the 1024x768 resolution using modeline it shows up (and actually comes with some predefined values which seem to work really well, i.e. overscan is negligible).

  Regarding the blue hue on everything I found this link [[COLOR="Red"]here[/COLOR]]("http://www.avsforum.com/avs-vb/archive/index.php/t-847670.html") which indicates (bottom of page) that the "TVOutFormat" does take "Component" as a value and that supposedly fixes the blue hue.  I just tested it quickly and using the modeline of 1024x768 nothing came up on the TV.  But I need to play around some more.

  I'll post my results (good or bad).

  IceCap

---

### Post by IceCap on 2010-04-03
I spent couple of hours last night working on my xorg.conf file and basically got nowhere but I feel like I have better understanding of my issues.
  First, looking at the X log file it appears that the supported resolutions are 

  1920x1080
  1280x1024
  1024x768
  800x600
  640x480

  but given that it is a CRT I'm not sure what that means.

  The "TvOutFormat" option seems to be critical.  I removed my xorg.conf, ran nvidia-xconfig which results in xorg.conf without "TvOutFormat" option and it gave a pretty nice 1024x768 60Hz screen but it had a blue tint.  If I put it to "AUTODETECT" or "COMPOSITE" I get the same thing (so obviously the default and AUTODETECT goes to COMPOSITE).  If I put it to "SVIDEO" I get red tint.  Clearly, I need it to be "COMPONENT" since I'm using component.

  However, if I set it to "COMPONENT" and otherwise use exactly the same xorg.conf that the nvidia-xconfig generated, I get nothing.  My understanding is that selecting "COMPONENT" you "default to a HD signal" and the 1024x768 isn't a proper HD resolution.

  So, then I kept Option "TvOutFormat" as "Component" and it seems that the only way to get something on the screen is to use the TVStandard option.  The HD720p doesn't work at all (green screen).  The HD480p works but I'd like to get higher resolution than 640x480 even though all my viewing is going to be in SD.
  When I use HD1080i I get what I believe is 1920x1080i but the refresh rate is only 30Hz and there is some underscan (believe it or not).  If I try to force a lower resolution (say 1024x768, they all have similar results) while still using HD1080i as TVStandard I get a 1024x768 window in the middle of the 1920x1080 screen.

  Even though this is a CRT I have the feeling that 1024x768 is the "natural" resolution and I'd like to get that resolution but the COMPONENT TVOutPutFormat forces me to use predefined resolutions (it appears).

  I'm not sure if anyone can really help me with this since few people still are using CRTs for TVs but if someone could direct me to a good tutorial I'd appreciate it.  The nvidia README file lists what each option does but it doesn't really put it all together and explain how to make a working xorg.conf file.  The xorg.conf manual page does that but it doesn't look like it covers the nvidia drivers.

  Thanks

  IceCap

---

