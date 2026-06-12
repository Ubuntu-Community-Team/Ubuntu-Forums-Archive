---
title: "Problem:  Poor display resolution"
date: 2009-04-26
forum: Multimedia Software
---

### Post by BlueFortress on 2009-04-26
Hi,

I've freshly installed Kubuntu 9.04, and the available display resolution seems poor and I cannot seem to fix it.

When I go to System -> System Settings -> Display, the highest resolution listed is 960x600.

My monitor is a Dell 1905FP LCD display, which I believe I have successfully used with Kubuntu in the past.

My graphics card is an SiS 315PRO, which should be OK, too.

Running lspci -v indicates:

```
02:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 315PRO PCI/AGP VGA Display Adapter
        Subsystem: Elitegroup Computer Systems Device 0c26
        Flags: bus master, 66MHz, medium devsel, latency 71, IRQ 11
        BIST result: 00
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at ff9c0000 (32-bit, non-prefetchable) [size=256K]
        I/O ports at dc00 [size=128]
        Expansion ROM at ff9b0000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: sisfb
```

When I run xrandr, I receive the folllowing output:
```
Screen 0: minimum 320 x 240, current 768 x 576, maximum 960 x 600
default connected 768x576+0+0 0mm x 0mm
   960x600        60.0
   960x540        60.0
   800x600        60.0     56.0
   768x576        60.0*
   720x576        60.0
   856x480        60.0
   800x480        60.0
   720x480        61.0
   640x480        60.0
   400x300        60.0
   320x240        61.0
```

So, that would seem to suggest that my Dell 1905FP monitor is not being correctly recognized or accepted for some reason.

The output of my /var/log/Xorg.0.log gives the following clues:

```
(II) SIS(0): VESA VBE DDC supported
(II) SIS(0): VESA VBE DDC Level none
(II) SIS(0): VESA VBE DDC transfer in appr. 0 sec.
(II) SIS(0): VESA VBE DDC read failed
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 253 MHz
(II) SIS(0): Replaced entire mode list with built-in modes
(II) SIS(0): Using real widescreen modes for CRT1 VGA devices
(II) SIS(0): 	Use option "ForceCRT1VGAAspect" to overrule
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) SIS(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) SIS(0): Unable to estimate virtual size
(II) SIS(0): Clock range:  10.00 to 253.06 MHz
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x400" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "320x200" (vrefresh out of range)
(II) SIS(0): Not using default mode "512x384" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1400x1050" (hsync out of range)
(II) SIS(0): Not using default mode "1400x1050" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "856x480" (hsync out of range)
(II) SIS(0): Not using default mode "1360x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1680x1050" (hsync out of range)
(II) SIS(0): Not using default mode "1280x854" (hsync out of range)
(II) SIS(0): Not using default mode "1280x854" (hsync out of range)
(II) SIS(0): Not using default mode "1280x854" (hsync out of range)
(--) SIS(0): Virtual size is 960x600 (pitch 960)
```

I've tried editing my /etc/X11/xorg.conf file, but it automatically seems to revert to its original form following reboot:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```


Can anybody please help me identify the cause of this problem and suggest a resolution?

Thanks very much!

---

### Post by inobe on 2009-04-26
hi

i am sorry to say but sis has been long ignored by the vendor' i did do some research even if it was probably helpless and found

[http://www.lemis.com/grog/HOWTO/mythtv-setup.html](http://www.lemis.com/grog/HOWTO/mythtv-setup.html)

ignore everything else and focus only on steps 7 and 10.

-----------------------------------------------------------------------

does your computer have a agp slot ?

if so' purchase an nvidia agp card 6xxx series and up.

---

### Post by BlueFortress on 2009-04-26
> **inobe said:**
> i am sorry to say but sis has been long ignored by the vendor' i did do some research even if it was probably helpless and found

[http://www.lemis.com/grog/HOWTO/mythtv-setup.html](http://www.lemis.com/grog/HOWTO/mythtv-setup.html)

ignore everything else and focus only on steps 7 and 10.


Thanks very much for your suggestion, but it did not seem to resolve my issue.  (I'm not sure that the info/drivers on that site are completely up-to-date.)

It seems unfortunate to me that (lack of) SiS drivers might be the source of this problem and no solution is available.  But I haven't given up yet.  I'll keep looking for a solution to this issue.

Thanks again.

---

### Post by inobe on 2009-04-26
search the forum for that graphics chip, i did and came up with no results, you may find something useful :)

---

### Post by BlueFortress on 2009-04-26
I tried replacing my video card with an old Nvidia card I had lying around:

```

02:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)
        Subsystem: nVidia Corporation Device 002e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at feaf0000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: nvidiafb, rivafb

```

But that didn't seem to change anything.  I still only see a very poor selection of display resolutions available.

---

### Post by BlueFortress on 2009-04-26
I've also tried manually adding my monitor info in /etc/X11/xorg.conf , as some have suggested in other forums.

```

Section "Monitor"
        Identifier "DELL 1905FP"
        VendorName "DELL"
        ModelName "1905FP"
        HorizSync 31.5-48.5
        VertRefresh 40-70
        Option          "DPMS"
EndSection
```

But when I check System Settings -> Display, I still only see "default" display with very minimal/poor display resolutions available.

This is kind of frustrating...  I've used this same monitor and these same video cards with previous versions of Kubuntu with no problems in years past, iirc.

---

### Post by inobe on 2009-04-26
the new xorg/ xserver is pretty redundant and drivers for these graphics cards do mostly everything.

if you noticed your xorg.conf it was probably empty !

now i would suggest running debian then building the desktop, the xorg.conf can be easily edited or it may even detect the graphics chips.


i remember running deb in the past, it was kinda nice, it didn't detect my card but was able to modify xorg.conf on the fly and the results were great.

i wish i could offer more solutions.

---

### Post by inobe on 2009-04-27
> **BlueFortress said:**
> I've also tried manually adding my monitor info in /etc/X11/xorg.conf , as some have suggested in other forums.

```

Section "Monitor"
        Identifier "DELL 1905FP"
        VendorName "DELL"
        ModelName "1905FP"
        HorizSync 31.5-48.5
        VertRefresh 40-70
        Option          "DPMS"
EndSection
```

But when I check System Settings -> Display, I still only see "default" display with very minimal/poor display resolutions available.

This is kind of frustrating...  I've used this same monitor and these same video cards with previous versions of Kubuntu with no problems in years past, iirc.

whoa' i noticed you don't have any modes in there or depth!

example only

```
Section "Monitor"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1024x768"
        EndSubSection
EndSection

```

---------------------------------------------------------------------------------------------------------------

edit: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)


it's old but a lot will help you

---

### Post by BlueFortress on 2009-04-27
Nope.  Still doesn't work.
 
But thanks for your suggestion.
 
I notice a lot of other people are reporting this issue, as well.
 
This display resolution regression and the removal of standard configuration tools and changes in default behavior is a very big step back, imo.
 
(Stuff like this makes me feel like Kubuntu is constantly "evolving" but never really improving.  : (    For example:  Why doesn't my machine even shutdown or reboot cleanly in Kubuntu 9.04?  How many years does it take to get that functionality ironed out?  : (
 
Sorry, just very frustrated...  : (

---

### Post by inobe on 2009-04-27
a debian minimum install then build it.

---

