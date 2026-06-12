---
title: "Help configure vga out for crt tv"
date: 2008-12-06
forum: Multimedia Software
---

### Post by shmish on 2008-12-06
Hi,
I'm trying to use my vga out port to connect to my crt tv.  I've used this port to connect to a lcd monitor and it worked without issue.  However, I haven't had any luck with the crt tv.

My video card is an ATI x700 with the envyNG driver.  I connect to the tv using a VGA to Component cable.  My /etc/X11/xorg.conf is:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

I have the ATI Catalyst Control Center in Accersories, but it doesn't work (doesn't open when I click on it).

I'd think I should be able to manually edit xorg.conf?  But I really don't know what to add.

thanks!

---

### Post by shmish on 2008-12-06
I managed to get the Catalyst Control Center working.  I had to delete this line in xorg.conf, it was giving an error:
```
Disable	"dri2"
```

So when I boot with the tv hooked up I get two displays recognized in CCC. 
1. [Default Monitor] ATI RADEON X700, Display Type = Analog Monitor
2. [Default Monitor] ATI RADEON X700, Display Type = Laptop Display

Furthermore, found some code for xorg.conf:
```
Section "Screen"
Identifier "Television Screen"
Device "Television Device"
Monitor "Television"
DefaultDepth 24
Option "TVOutFormat" "COMPONENT"
Option "TVStandard" "NTSC-M"
SubSection "Display"
Depth 24
Modes "nvidia-auto-select"
EndSubSection
EndSection 
```

I wonder if I can adapt some of this for my xorg.conf.  I'm not sure if this would affect my regular display when the tv is not hooked up.  Furthermore, I don't really know what the correct entries for me would be, for things like Device, Monitor, Indentifier, etc.

Any advice is appreciated.

thanks

---

### Post by CHaoSlayeR on 2008-12-10
First of all the code you found only applies to nVidia cards so I wouldn't expect any success here.

For switching the TV on or off you can use the **aticonfig** utility in a terminal.

Just type **aticonfig --help** to get all options with descriptions.

The relevant options for the TV setup should be the following (assuming fglrx driver 8.10+):
```

TV Options:
  --tvf, --tv-format-type=STRING
        Change the TV signal format.  STRING can be one of:
           NTSC-M
           NTSC-JPN
           NTSC-N
           PAL-B
           PAL-COMB-N
           PAL-D
           PAL-G
           PAL-H
           PAL-I
           PAL-K
           PAL-K1
           PAL-L
           PAL-M
           PAL-N
           PAL-SECAM-D
           PAL-SECAM-K
           PAL-SECAM-K1
           PAL-SECAM-L
        Note: Not all graphics cards support every mode. Regional
              settings are applicable.
  --tvs, --tv-standard-type=STRING
        Change the TV standard for TV output.  STRING can be one of:
            VIDEO
            SCART
            YUV
 --tv-overscan={on|off}
       Enable or disable overscan mode for TVout
       Note, not all tv-formats support overscan. Try to
       toggle overscan off before changing tv-format if
       and error occurs.
 --tv-info
         Print out the current tv geometry, tv format, and if the
         tv is physically connected.
 --tv-geometry=WIDTHxHEIGHT{+|-}X{+|-}Y
              =WIDTHxHEIGHT
         Change the size and position of the TVout display.
         WIDTH and HEIGHT are in percentage units. Please note
         that the valid range for WIDTH and HEIGHT depends on
         the tv-format selected. However, as a rule of thumb
         WIDTH and HEIGHT are valid in the range [1,100]
         X and Y are pixels offsets from centre
         of the screen. X and Y are have variable ranges dependant
         on ASIC. Use tv-info to get valid X and Y ranges
         If tv-geometry is invoked with just width and height
         then X and Y are assumed to be 0
         See example 5 below for a sample usage.

```

To switch the TV **on** this command should do it (assuming you have a regular CRT as the primary display):
```

aticonfig --force-monitor=crt1,tv

```

To switch the TV **off** this command should do it (assuming you have a regular CRT as the primary display):
```

aticonfig --force-monitor=crt1,notv

```

If all goes well you shouldn't need to edit the xorg.conf manually again.

Regards,

C]-[aoZ

---

### Post by shmish on 2008-12-10
Thanks for the reply.
I was trying some of those options this week without much success.  I was getting a signal on the tv but the image was really messed up.  I set the --tv-standard-type=YUV, and the only thing I haven't tried yet is changing the geometry.  The tv is showing mostly a dark screen with some gray elements in it (elements = distorted chunks and pieces of the desktop).  I'm using a VGA to component adapter cable, perhaps this system isn't really compatible with my computer/tv.

As luck would have it, I'm now having problems running ubuntu on the computer without the tv hooked up. I'm not getting any picture.  I've booted into recovery mode and ran aticonfig --initial, rebooted, and still have the problem.  I think the ATI Catalyst Control Center is taking control of the video (ie the xorg.conf is deprecated?), so even though I restored xorg.conf, the display is still out of wack.

I'll play with it for a while and see what happens...

---

### Post by CHaoSlayeR on 2008-12-10
OK, the problem with modifying the xorg.conf and the changes not getting applied by the driver is one of the flaws that ATI uses another configuration file in an really terrible format that must be in sync. Many have problems with that. To be sure the changes you made to xorg.conf are getting applied type the following:
```

aticonfig --input=/etc/X11/xorg.conf --tls=1

```

Regarding your TV problem I think with your specific setup using an adapter cable you shouldn't configure a TV for the fglrx. I wasn't taking all the information in mind you provided in my previous posting. So it is best to revert to the configuration you initially had using the autodetect functionality of the fglrx driver.

After that we should just define exactly **one** modeline for the TV.

You have two ways to get one:
1. Try an appropriate one from the [MythTV project]("http://www.mythtv.org/wiki/index.php/Modeline_Database")
2. Get technical data about your TV and calculate one using [this generator]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")

After that we have to set up the xorg.conf appropriately. I'm assuming that you want to use the TV as additional Desktop space and drag the video on it to display them in fullscreen while you are working on the primary. This is relatively "easy" as you just have to create an initial dual-head config with the aticonfig tool (specifying the TV as "crt" and **not** "tv") and then you just add the specific modeline into the **monitor** section that represents your TV. To be sure you should also turn off EDID by inserting the following option in the **device** section:
```

Option "IgnoreEDID" "true"

```

Then you should be getting a good picture on your TV. I've seen others that did it this way but never tried it myself. However I do have such cables around here too so if you're not into much luck I could try to configure it myself and afterwards giving you an appropriate how-to. But that also depends much on the mood of my girl friend if I am able to abuse her computer for that task as the computer I am working on is a laptop with an nVidia card and that wouldn't be of much help here.


Best regards,

C]-[aoZ

---

### Post by shmish on 2008-12-11
Hey, cheers for all the help.  I'll definitely dig into it this weekend.  One thing though, I'm hoping to clone my desktop.  I recall seeing the clone option in aticonfig, and I used this in some of my earlier trials.  For some reason when I had dual monitors enabled, the desktop was automatically extended.  So when I was using the computer, my mouse could scroll way off the screen to the right.  Is it the double 0 that creates this type of desktop?
```
Screen 0 "aticonfig-Screen[0]" 0 0
```
or maybe the viewport?
```
Viewport 0 0
```



BTW, the goal for this project is so I can run XBMC on the computer and output it to my tv.  The picture quality (resolution I guess) on the computer screen would not be important.  It would be a lot easier if I had a LCD tv, that's for sure!  

thanks

---

### Post by CHaoSlayeR on 2008-12-11
What type of TV you have is not the point. The main point is what connection types are understand by the TV. As modern TVs also have Sub-D or DVI connectors that should be much easier to set up indeed.

None the lines you mentioned actually "cause" that the mouse can go off the screen to the right. It is just the configuration of the desktop size that exceeds the resolution of your primary monitor and because of the "viewport" setting it is set to the top left corner (0 0 means x=0 and y=0). Therefore if you don't have specified that your TV is on the left side of your primary monitor the exceeding space is always added to the right of your primary monitor.

If you just want to use your secondary monitor for video output I don't know which program to use for this. Before I had an ATI card I always had Matrox cards and they do that automatically when enabling an option for the driver plus the Matrox cards always delivered the best picture on TVs one could get out of a computer. Anyway your card really doesn't have a TV-out or something? Not even a connector for that on the graphics board? I thought the last one without any of that shipped ages ago. Even my lousy HD2400 has one DVI, one Sub-D, one HDMI and one S-Video connector.

Well, then your only option is using the specific monitor modeline I think.

Regards,

C]-[aoZ

---

