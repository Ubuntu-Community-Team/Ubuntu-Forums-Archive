---
title: "1440x900 resolution with i810 (865G) in L194WT"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by mkuutti on 2007-02-17
I recently bought small-form-factor Dell Optiplex GX270 as compact and silent workstation. It seems to have integrated Intel graphics controller with 865G chipset. It uses i810 driver for X. I installed Windows and got perfect setup with my LG 19" widescreen LCD display. After installing Kubuntu Edgy i got only stretched 1280x1024 resolution, none of the widescreen modes were available. My previous workstation with Nvidia 6600 (connected to DVI) did 1440x900 without problems. Again, integrated devices gave me a headache. 

I downloaded Feisty RC4 and it gave me same results. 

I googled and found out that I needed to specify modelines manually to achieve 1440x900. I copied modeline (googled Modeline 1440x900@60) and found out that i810 driver did not support such mode 1440x900 (/var/log/Xorg.log.0). Googled again and found tool called 915resolution (sudo aptitude install 915resolution) which will patch i810 driver's currently supported modes to something else. (sounds like a hack to me). "*sudo 915resolution -l*" gave list of modes (none widescreen) and I tried to patch them one by one (editing /etc/default/915resolution) to find suitable mode to patch. When patching mode 38 (1280x1024) my X started with 1440x900 resolution (checked with xvidtune) BUT my screen was not perfect at all. There was about 20% black in a top of screen and image was way too wide. Tried plenty of Modelines found from internet but all gave me same result.

I'm trying to explain what I did to get for successfull mode:

1. Modeline check. My Windows had correct timings so I installed PowerStrip and checked timings : 
[I]Click the Powerstrip tray icon and select "Display Profiles" -> "Configure".
 Select the "Advanced timing options" button.[/I] It showed all current timings, and when clicked "copy to clipboard" button it made Linux modeline row for me :)  It was slightly different than Modeline I had so I tested it. No success, still 20% black and image way too wide. So it was not my modeline what was wrong.

2. Driver check. This was the problem: I noticed that 915resolution had commandline options [htotal] [vtotal] which /etc/default/915resolution did not use. There it was, my driver propably used htotal and vtotal from 1280x1024 mode! I ran manually *sudo 915resolution 58 1440 900 32 1904 934* and restarted X. It actually was 1440x900, little too much right, though. 
**EDIT:** seems that it's still not ok, picture is not sharp at the right side of display. Damn. Anybody help. Plz.

3. Fix */etc/init.d/915resolution* and */etc/default/915resolution* to support htotal and vtotal. 




Shortly

1. aptitude|apt-get install 915resolution

2. edit /etc/X11/xorg.conf:
```
...
Section "Monitor"
...
  Modeline  "1440x900@60" 106.40  1440 1520 1672 1904  900 903 909 934 -Hsync +Vsync
...
Section "Screen"
...
  modes "1440x900@60" ...

```

3. run 915resolution manually to test :
*sudo 915resolution 58 1440 900 32 1904 934*

4. restart X. If everything is working, continue to step 5.

5. patch 915resolution files for your modes
I added 2 params to */etc/default/915resolution* :
```

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
#MODE=auto
MODE=38
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32
#
# own additions
# htotal and vtotal
# these are optional BUT you MUST specify BIT variable if
# these are used. You will also have to specify both of these
HTOTAL=1904
VTOTAL=934

```
and following to */etc/init.d/915resolution*:
```

...
case "$1" in
  start|restart|force-reload)
        echo -n "Starting $DESC: "
        if [ "$MODE" = "auto" ] ; then
            auto_select_modes
        else
            $PROG $MODE $XRESO $YRESO $BIT $HTOTAL $VTOTAL
        fi
        echo "$NAME."
        ;;
  stop)
...

```

6. Reboot and check that everything is working

Does anybody know if it's possible to include these widescreen modes to i810 driver instead than using these hacks? 

NOTE: modelines and 915resolution modes are from my system, please use settings from your own system.

---

### Post by mkuutti on 2007-02-17
Because picture is still not what I want, I'll try next to disable DDC and patch 1024x768 mode, reporting results here...

EDIT: I really should send screenshots here, results are quite funny... 1024x768 mode actually worked, picture is sort-of-an fullscreen, but about 5% of screen ( vertically from left ) was missing and appears at the right side of display. To access Kubuntu's K-menu I had to look at the lower right corner and move mouse pointer to lower left corner...

I might try debian's xorg 7.2 packages, but that means that I should upgrade my whole X. I just noticed that there is xserver-xorg-video-i810-modesetting package, I'll check out that first.

EDIT2: modesetting driver won't work with my chipset i guess. Anyway, moving this to thread: [http://ubuntuforums.org/showthread.php?t=203905]("http://ubuntuforums.org/showthread.php?t=203905"), cause it's about same problem.

---

### Post by swift&amp;smart on 2007-02-21
Hello,**mkuutti**. I am new here in this forum.

As the same as you,I use L194WT as output for my DELL notebook at home.However,I did try various methods to display 1440x900 on the LCD monitor but without success.What do you think of the cause?Have you ever tried the Intel driver?I did.However,it failed to compile and it seems like there are no user used original driver from intel but module i810.Anyway,maybe you can take a look at this website if it helps.[Intel Graphic Card]("http://www.intel.com/support/graphics/sb/CS-022544.htm")

**mkuutti**,I did think about is there any relationship between the wide screen monitor and the version of X11.As far as I know,Fedora Core 6 uses X11 version 7.0 in LiveCD. As a result,I will try this LiveCD tonight and see if it can display th optimal resolution.If it does,we can refer to the setting of xorg.conf or any clues in it.

Hope we can solve this problem.:)

---

### Post by mkuutti on 2007-03-03
Amazing things happen nowdays. 

I found pbrockway2's thread  [(Another) Widescreen tale of woe ]("http://ubuntuforums.org/showthread.php?t=368204")  and was pleased that our advices were helpful. I ended up to solution that configuration he used was best available for me too, even though:

1. My screen was initially way too much on the right side
2. After adjustment left side of screen was sharp but "overcontrasted" and right side was less contrasted and unsharp, f.e. konsole fonts were hardly readable.

Anyway, I had 1440x900 and I thought that what a heck, my new Matrox is on it's way, this is good enough for me. I have dual-boot system and I discovered my display has "auto set" functionality (button above powerbutton) which I used between OS-boots. Today, I booted (accidentally) to Kubuntu and, again, pressed "auto-set" button which started moving screen even more to right (!), and after 3 or 4 movements, screen was centered and image is perfect! No contrast problems, whole screen is sharp.

I'll never shutdown my system :)

My advice: Keep on pressing that button, it will save the world.

Case closed!

EDIT: This configuration works fine, but sometimes I need to press monitor autoset several times to get sharp picture, so it's my monitor which causes the problem, not the driver. I'll get my G550 today and it'll have DVI connector, hopefully that makes better quality than VGA.

---

### Post by andrew.46 on 2007-03-21
Hi!

 Is there a known problem with this computer (I am about to buy one!) where the BIOS has to be changed to allocate 8 megs RAM to the card?

                        Andrew

---

