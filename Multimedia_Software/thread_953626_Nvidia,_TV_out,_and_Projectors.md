---
title: "Nvidia, TV out, and Projectors"
date: 2008-10-20
forum: Multimedia Software
---

### Post by FEF on 2008-10-20
All,

I've been playing with Ubuntu for about a year, and I've been battling this issue off and on for a few months.  Ubuntu's a class act, but it's times like this where I want to pull the rest of my hair out.  :)

From the Nvidia forums:
-----------
All,

I have an interesting problem getting a few pieces of hardware to work together. The pieces are:

Infocus Projector using S-Video in
Pinnicle PCTV HD PCI
GForce 7300GS PCIe using S-Video out (TV-out)
Win XP, and I have the problem in Ubuntu, too

The main issues are:
The projector won't operate at 60hz refresh rate.
The TV card won't show the TV on anything but the primary monitor
The Video card won't allow me to have the single (TV S-video out) monitor in anything other then 60Hz.

The Projector works in Clone and Dual view, but when I boot up with TV out alone, the refresh rate defaults back to 60Hz. After getting it to work in Clone mode, it forgets the settings when rebooting after disconnecting the LCD.

Is there a Registry tweak or something that can help me force the TV out to boot at 70+Hz (120Hz would be best, I think)

Thanks for the help
-----------------------------
That was with Windows.  As I really want Ubuntu (or MythBuntu), I guess this is the place I really want to be.

Now to the point... as this PC is only running the porjector from the TV out, I don't need/want any kind of multi-monitor setup.

The big problem is that when I crtl-alt-bkspc it works fine, but when I reboot I get the low video settings dialog box, and the Nvidia drivers are uninstalled.

I'm not on the MMPC right now so I don't have the exact xorg.conf, but it's something like this
```

 Section "Monitor" 
    Identifier "Monitor"
    HorizSync 30-50
    VertRefresh 70 
 EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device" 
   	Option          "TVOutFormat" "SVIDEO" 
   	Option          "TVStandard" "NTSC-M" 
   	Option          "ConnectedMonitor" "Monitor" 
   	BusID           "PCI:2:0:0" 
EndSection

Section "Screen" 
   	Device "Device" 
   	Identifier "Screen" 
   	Monitor "Monitor" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_70" 
       	EndSubSection    
EndSection

```
This is a veriant from [http://ubuntuforums.org/showthread.php?t=98456]("http://ubuntuforums.org/showthread.php?t=98456").  That's the TV out for Newbies thread...

The bottom line is that I need the TV out to stick at a refresh rate over 70Hz.  These projectors won't work at 60Hz, which is what the TV-out assumes everyone needs.

It's an interesting problem.

Thanks in advance,

---

### Post by aeiah on 2008-10-20
are you using nvidia-settings in ubuntu? if you can set what you want there but it isnt saving the settings, make sure you're running it as root
```
sudo nvidia-settings
```

if that fails, perhaps you can look into setting it up in windows using a mixture of the nvidia control panel and powerstrip, and exporting the powerstrip settings as a linux modeline, which you can then paste into your xorg.conf file in the Monitor section along with vert and horiz refresh information

my monitor section looks like this. it'd be crazy to copy all but the structure though:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AOC L32W451"
    DisplaySize     1600    900
    HorizSync       31.0 - 50.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1240x692" 69.2 1240 1296 1424 1608 692 693 696 717 +hsync +vsync
    Option         "IgnoreEDID" # you may or may not want this bit
EndSection

```

---

### Post by FEF on 2008-10-20
I tried to get it going in Windows, after I wasn't able in Linux the first time.  I went from Ubuntu -> Windows -> Ubuntu in windows.  That's how I found out it's a Refresh Rate issue.

It appears to be a Nvidia driver issue.  The TV-out is a sore spot for many.  It's almost like the TV out is only able to 60Hz.  :(

I'll try the nvidia settings.  I think I've been there before, though.

OH!  I installed nvtv.  By the description, it's supposed to help with issues like mine.

It feels like it should be an easy fix.  It shouldn't be this hard to set the TV out to 70Hz.

:confused::confused:

---

### Post by cariboo on 2008-10-20
Your S-video out is never going  to be more the 60Hz, see this article:

[http://en.wikipedia.org/wiki/NTSC#Lines_and_refresh_rate](http://en.wikipedia.org/wiki/NTSC#Lines_and_refresh_rate)

it is a limitation of the system.

Jim

---

### Post by FEF on 2008-10-20
Ya, I read something like that a while back in school.  I would have dismissed the whole idea, except that it does work very well in Clone Mode.

I bought 2 different PC to TV converters, hoping it would be OK, but the S-video out is very crisp and clear when in Clone mode.  I can run the clone settings up to 120Hz before the Projector throws a fit.

Currently I have the VGA going to a PC to TV converter going to a video switch, the S-Video out going to the switch, then the switch goes to the projector.  I switch between the two to see if it's working.

I'd run in Clone out, but the Pinnicle card only work on the "primary" screen.  I got it to work in Windows in the Primary, never Secondary.  Didn't get it working with Ubuntu at all (with Mythbuntu), but I don't recall trying the TV card in Ubuntu clone mode.

So... If you run Clone monitors and make the VGA out primary, you can have 70-120Hz, but the TV card only works on the Primary monitor which is VGA-out.  If you make the TV primary (so it goes out the S-Vidio port), you only have 60Hz as an option.  Since the Projector doesn't like 60Hz, it goes blank and you can only see the VGA out... until you switch back to VGA-primary and change the Hz.

That said, I can see the "running in low-graphics most" popup.  It's not great, but it's there.  The system goes out the window when the video card driver is installed.  It appears the Video card is reminded that it's a TV out when the video driver is installed.  Though, I was running the Nvidia driver in Clone mode.

Maybe this is a better question: Can I fool the TV card into playing on the secondary monitor?  If so, I can leave the PC to TV converter on the VGA port, but only use the S-video.

Maybe another question: Can I force the clone mode settings (without actually Cloning the monitors)out the S-video port when not in Clone?

Thanks for the help.

---

### Post by FEF on 2008-10-21
The S-Video port does what I want, just not when I want it too.  Anyone have another thoughts?

---

