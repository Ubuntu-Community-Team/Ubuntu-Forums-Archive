---
title: "Samsung HDTV monitor low resolution"
date: 2010-08-03
forum: Multimedia Software
---

### Post by lofttroy on 2010-08-03
So I thought it would really neat to have a 32" monitor.  I got all fired up and found a pretty good Samsung HDTV (UN32C6500).

It's a dual boot machine and Windoze seems to work well at the screens native resolution (1920x1080).  I used the powerstrip program to pull the operating information from the hardware.

Graphics card: ATI Radeon X600 (RV380 chipset)

When I booted up Ubuntu 10.04 and xrandr'd no love.  It seem to be stuck in a mode that doesn't display.  I can get to my account by hitting enter when the screen goes black and typing in my password.

I xrandr'd until I thought my eyes would bleed.  No luck.

I pulled the edid using get-edid.  It reported an error, but would parse the fine, when I saved the file and parsed using parse-edid.

I've thought of using a custom EDID file, but I've also read that 10.04 doesn't require an xorg.conf (confirm true on my machine).

I'd appreciate any help on this; 1280x1024 on a 32" monitor is slightly annoying.

Thanks,

Troy

---

### Post by efflandt on 2010-08-04
If your video card has DVI it would likely work better (easier) using a DVI to HDMI cable (or HDMI if it has that).  Then it should be able to see the EDID of the display.  VGA often does not really see the EDID, so you would either need to use xrandr or create xorg.conf and add something to that (which I am not very familiar with).

So for laptops that sometimes connect to HDTV with VGA, I just create a shell script with xrandr command and put a launcher for it on desktop or top panel.  Either use **cvt 1920 1024** or **gtf 1920 1080 60** (or maybe 50 in europe) to find a modeline for xrandr.  Or I use a modeline similar to one found in /var/log/Xorg.0.log for a PC connected DVI to HDMI to a 1080p HDTV.

For example see if these commands work or get something close (you may need to use TV menus to see if you can sync display to it).  This assumes that xrandr with default ATI drivers sees your video device as VGA-0:

xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA-0 1920x1080_60.00
xrandr --output VGA-0 --mode 1920x1080_60.00

Otherwise try a modeline from cvt or gtf and see if that works better.  If you find something that works, create a script with those commands with a first line as follows, and make the script executable (chmod 755 scriptname):

#!/bin/bash

If you create a bin directory in your home directory (/home/username/bin) that directory will automatically be in your PATH the next time you login.

---

### Post by lofttroy on 2010-08-04
Thanks for the attempt.

More detail:

The TV is connected via a DVI HDMI adapter.  And the TV is setup correctly via menu options for computer.  I've verified this as it works flawlessly in the Windows.

My first attempts at xrandr were to use the values created by cvt and gtf.  These values are similar to the values listed in my TV's manual.  (Yes, it lists PixelClock, Hfreq, Vfreg, Hsync, Vsync).

I've tried the commands you've listed, changing VGA-0 for my own DVI-0 (where the cable is connected).

I've also tried multiple different values of modeline that work fine in Powerstrip.

---

### Post by james2c19v on 2010-08-06
I'm sorry that I can't suggest a solution, but I just wanted to say that I have a similar problem.  I have the exact same video card (ATI X600) and I can't get anything beyond 1024 x 768 to work on my 23'' HD display (Asus... though for whatever reason it's detected as Ancor Communications).

I'm using a dual-monitor setup on Lucid, and my laptop screen is fine, but my HD monitor connected over VGA goes on an acid trip whenever I use System > Preferences > Monitors to try to change the resolution to something higher.  I get 1920 x 1080 in Windows 7, but I've really been having it with the resource consumption these days.

---

### Post by james2c19v on 2010-08-24
Strange, but I was able to get 1920x1080 to work on my standalone LCD after I reduced the resolution on my laptop monitor to 848x480.  If I make the resolution higher on the laptop monitor, the standalone LCD either says "out of range" or it goes unreadable with fuzz and lines.

I was also able to get 1920x1080 to work *upside-down* while my laptop monitor was on a higher resolution.

I hope that someone intelligent can interpret what's going on...  

Again, this is the Radeon Mobility X600.

---

