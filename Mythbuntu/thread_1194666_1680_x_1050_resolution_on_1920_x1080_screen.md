---
title: "1680 x 1050 resolution on 1920 x1080 screen"
date: 2009-06-22
forum: Mythbuntu
---

### Post by scottac on 2009-06-22
Alright I am running dual monitors on mythbuntu 9.04. I have a chimei 22" monitor and a 32" Toshiba HD LCD. My graphics card is a nvidia 9500GT

When I reboot the machine myth frontend opens up on the 32" which is what I want it to do. However the resolution of the mythfrontned GUI is stuck on 1680x1050.  

Is there anyway to force mythfrontend to open up in 1920x1080.

I have attached a screen shot of the Toshiba LCD so you can better understand what is happenning.

Thanks in advance for all help.

---

### Post by crez79 on 2009-06-22
from mythfrontend --help maybe start it via ```
mythfrontend --geometry 1920x1080

``````
$mythfrontend --help
Valid options are: 
-display X-server              Create GUI on X-server, not localhost
-geometry or --geometry WxH    Override window size settings
-geometry WxH+X+Y              Override window size and position
-l or --logfile filename       Writes STDERR and STDOUT messages to filename
-r or --reset                  Resets frontend appearance settings and language
-w or --windowed               Run in windowed mode
-nw or --no-windowed           Run in non-windowed mode 
-O or 
  --override-setting KEY=VALUE Force the setting named 'KEY' to value 'VALUE'
                               This option may be repeated multiple times
-G or 
  --get-setting KEY[,KEY2,etc] Returns the current database setting for 'KEY'
                               Use a comma seperated list to return multiple values
-v or --verbose debug-level    Use '-v help' for level info
-p or --prompt                 Always prompt for Mythbackend selection.
-d or --disable-autodiscovery  Never prompt for Mythbackend selection.
-u or --upgrade-schema         Allow mythfrontend to upgrade the database schema
--version                      Version information
<plugin>                       Initialize and run this plugin

Environment Variables:
$MYTHTVDIR                     Set the installation prefix
$MYTHCONFDIR                   Set the config dir (instead of ~/.mythtv)
```

---

### Post by scottac on 2009-06-22
This works when I run the command. However when I reboot it reverts back to the 1680x1050 resolution. 

Does anyone know how to force the frontend to open in 1920x1080 by default?

---

### Post by crez79 on 2009-06-22
Have you tried to change the resolution in screen settings in setup->apperance or there abouts? Is it not remembering it? If i recall correctly that is how I set the resolution on one of my boxes.

---

### Post by scottac on 2009-06-23
At Utilities/Setup->Setup->Screen Setup Wizard there is a way to tweek the screen size but it won't go any bigger than 1680x1050.  

Is this how you were able to do it?

---

### Post by scottac on 2009-06-23
Bump.  There has to be a way to do this. I have been searching the web and can't find anything.

So when I disable the chimei 22" monitor in nvidia-settings I have no issue at all and mythfrontend is loaded in 1920 by 1080. but as soon as I re-enable the 22" it just goes back to 1680 by 1050. . There has to be a file somewhere that I can change to get the proper resolution.  

No one else has had this issue...

---

### Post by Caps18 on 2009-06-24
Are you using HDMI cables?

I had this problem before I replaced one PC-to-TV converter that would take HDMI signals to VGA and then convert them again to 640x480.  The HDMI to VGA converter's max resolution was 1280x1024 and it forced my 1920x1080 HDTV that was being split to it's smaller resolution.

I think I posted something about it before, but I spent the $500 to just get a new 1080p HDTV and fix the problem.

The other solution was to start the Mythbuntu computer with the smaller res monitor disconnected, and plug it in after it had been set at 1920x1080.

---

### Post by Caps18 on 2010-02-02
I just had this problem happen agian.  I had to choose plug & play for the monitor choice, and go into /etc/X11/xorg.conf and add 1920x1080@60 as a mode close to the bottom.

Then I needed to use the Control panel, go into the xorg config program and choose 1920x1080 @ 60 Hz.  It had it at 50 Hz and it didn't fill the screen.

---

### Post by matt06 on 2010-02-03
> **crez79 said:**
> from mythfrontend --help maybe start it via ```
mythfrontend --geometry 1920x1080

```

> **scottac said:**
> This works when I run the command. However when I reboot it reverts back to the 1680x1050 resolution. 

Does anyone know how to force the frontend to open in 1920x1080 by default?

I don't remember where I found this, but here is what I have in my notes about using the --geometry option when I set up my 9.10 frontend and had to resize/reposition it on an old SD TV. (using SVideo to composite converter)

to fix frontend location and size edit /etc/mythtv/session-settings then add to end MYTHFRONTEND_OPTS="--geometry widthxheight+horpos+vertpos" example:

```
MYTHFRONTEND_OPTS="--geometry 936x720+35+27"
```

And here is the full session-settings file I used:

```
###############################################################################
# This file is used if /usr/bin/mythfrontend is called with --service         #
# as in mythtv.desktop which ships with the mythtv-frontend package           #
###############################################################################

# Enable mythwelcome
# Note: if you enable this, MYTHFRONTEND_OPTS is ignored
# You will have to specify your startup options for mythfrontend in mythwelcome
#
# Note: a log file is available at /var/log/mythtv/mythwelcome.log
# which should also include mythfrontend output
#
# MYTHWELCOME=true

# Startup options for mythfrontend
# "--verbose all,nodatabase" is just an example. You will get LOTS of output!
# To obtain a list of verbose levels, run "mythfrontend --verbose help"
# To find out more about other available options, run "mythfrontend --help"
#
# Note: a log file is already available at /var/log/mythtv/mythfrontend.log,
# so there's no need to specify --logfile (or -l) unless you want to log to a
# non-standard location
#
# MYTHFRONTEND_OPTS="--verbose all,nodatabase"
# add geometry option to position screen
MYTHFRONTEND_OPTS="--geometry 936x720+35+27"
```

In the end I used the frontend resizing options instead of the session-settings method, but it did work for me.

---

### Post by Caps18 on 2010-02-03
I am having the same problem that the OP was having now.  My computer "Forgets" about the changes I made to the xorg.conf after the second time I reboot.  I make the changes by adding in the line into the xorg.conf and say it should be 1920x1080@60, I restart and pick that, change the hertz to 60Hz and it is perfect.  When I restart again it goes back to 1680x1050 (even though it says it is an LCD panel 1920x1080, it is not an option).

Why would the OS or nVidia be reverting back to the original xorg.conf that is wrong?

---

### Post by LowSky on 2010-02-04
what command are you using to edit xorg or nvidia-settings?

---

### Post by Grenage on 2010-02-04
Most of these issues are down to the Twinview EDID bug, which can be circumvented by saving the EDID locally and referencing it in xorg.conf.

---

### Post by Caps18 on 2010-02-12
I'm just using vim to edit this:

> Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1680    1050
                Modes           "1680x1050@60"  "1600x1024@60"  "1440x900@60"   "1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"    "800x600@56"
        EndSubSection
EndSection


to this:

> Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1920    1080
                Modes           "1920x1080@60"  "1680x1050@60"  "1600x1024@60"  "1440x900@60"   "1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"    "800x600@56"
        EndSubSection
EndSection


It works the first time I restart (I still have to choose it, but it does show up as an option for a 1920x1080 LCD panel monitor.  Why it wouldn't be there by default is unknown to me.

I have tried to add this modeline in the xorg.conf file to see if it changes anything

"1920x1080@60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 +hsync +vsync

And I believe it worked with my previous video card because it could detect the screen.  So I may need to figure out how to fix the EDID issue.  That is probably the permanent solution.

Thanks

---

### Post by Grenage on 2010-02-13
Aye those modelines normally sort it for me.  I have a rough guide [here]("http://www.grenage.com/xorg.html"), but it sounds like you've nearly got it sorted.

---

### Post by Caps18 on 2010-02-15
I haven't had to restart it in a few days (I've been watching or recording the Olympics), but I did change the xorg.conf to 444 (Read-only).  We shall see if there is some programs that thinks it should have more control than root...

I do use three different 1920x1080 screens at home (3 rooms, two LCD, one projector and all connected to a HDMI switch), and one at work.  Everything worked with my old 6200 video card, but the built in one and reinstalled 190 driver isn't quite right yet (as of last week).

---

### Post by Caps18 on 2010-02-16
It still goes back to 1680x1050, even though I have set xorg.conf to read only...  I might have to consider going with 10.4 when it comes out to fix the problems I have now (no remote, audio device switches between dsp2 and ALSA:default, and X doesn't get the resolution right).

---

