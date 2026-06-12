---
title: "Video playback @ 1920 x 1200 (16:10) resolution"
date: 2010-03-27
forum: Multimedia Software
---

### Post by cmuxed on 2010-03-27
Sup peeps,

I have a HP 2140 Netbook running Karmic / 9.10 Ubuntu @ 1920 x 1200 (16:10), very smoothly might I add.  However... when I attempt to play a video file, it will play only the sound and leave a blank screen; regardless of the application (Banshee, avidemux, vlc, etc) or video file type (mpeg4, avi, etc).  If I lower the resolution to say; 1024 x 768 (4:3), then the video will appear.  In case you are wondering, I do have a 26" ASUS LCD connected in extended (not mirrored) mode via a Belkin KVM.

The graphics card details:[INDENT]```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
```

[/INDENT]Does anyone have any ideas how I can get this silly thing to stop annoying me?  Even though this is not a machine I sit and regularly watch videos at, I would rather not change the resolution just to watch a clip or test a rip etc.

Any ideas?  All the threads and relentless searching seems to keep refering me to dudes who have problems changing resolutions.  I can change the reso, its just my card does not seem to want to play movies at 1920  x 1200!

Cheers!

---

### Post by cmuxed on 2010-03-27
Although it is not a solution, I have installed resapplet to speed up resolution changes.  It adds a little icon on the top panel.

apt-get install resapplet

---

### Post by efflandt on 2010-03-28
Have you tried turning your netbook display off with xrandr before trying to display video on the external display?  But you would probably need to set mirrored mode or the external display as primary before doing that.

For my laptop with older Intel 945 video, I just boot up, BIOS and grub use the external display and then gui login comes up on both displays (in matching 1024x768).  Then I select one of two desktop launchers from X that uses xrandr commands in a script to switch to resolution of the external display (1360x765 or 1920x1080 which makes background image on laptop display very large) and the script switches off my laptop display (xrandr --output LVDS1 --off).

---

### Post by cmuxed on 2010-03-29
> **efflandt said:**
>  (xrandr --output LVDS1 --off).

Thanks efflandt, I have been mucking around with xrandr and by switching off my extended mode (i.e. the netbook display LVDS1), the video does appear, however when I switch it back to extended mode, the video blanks out again.  I'll keep playing with it and see what I can do.

What I have tried so far:[INDENT]```
sudo xrandr --output LVDS1 --off  < as expected, netbook screen is disconnected
sudo xrandr --output LVDS1 --auto < massive mirrored display on netbook
sudo xrandr --output LVDS1 --left-of VGA1 < back to reality (1024x576)
```
[/INDENT]I'll post my result soon! :D

---

### Post by cmuxed on 2010-03-29
After re-reading my posts, I thought I had better be more literal with the reason for me posting this topic.

I want to have at the same time in extended mode, my netbook running at 1024 x 768 and my external vga lcd running at 1920 x 1200 and be able to play videos ...without the video output being blank, of course!

---

### Post by cmuxed on 2010-03-29
Ok so dj-weird is in the house:  I was mucking around with the xrandr commands and used the --output -above VGA1 option and the video continued to work.  I then commanded it back to left-of and it disappeared again!

---

### Post by cmuxed on 2010-03-29
I am satisfied with using these two commands for now:[INDENT] ```
xrandr --output LVDS1 --off 
xrandr --output LVDS1 --auto --rotate normal --pos 800x0 --output VGA1 --auto --rotate normal --above LVDS1
```

*it doesnt seem to work without switching the LVDS1 screen (netbook) off first*

[/INDENT]I'll put them into a startup script... not that she reboots often ;)

It is not exactly how I would like it though, as with this configuration I can only utilise below or above... the left-of or right-of settings don't work.  When I have more patience, I could play around with manually setting this, but if anyone has a better understanding of xrandr, then your assistance would be appreciated.  I am reading through the man pages but I havent the full grasp as of yet...

Cheers!

---

### Post by cutterx on 2010-04-29
I'm having The same problem with my MSI Wind U123 which has the video chipset Intel 945gse (950gma graphics core). I'm running Ubuntu 10.04 and when I activate extended display on my 1080p lcd tv video will only play sound and black video when I set the extended display's resolution to anything above 1024x768. I tried the extended desktop in Windows XP and video plays just fine at full resolution. I'm not sure if its just an Intel chipset issue for Ubuntu or an extended display issue.

---

### Post by P_Squiddy on 2010-06-16
I've experienced this identical issue with two types of laptops: a Dell mini 9, with an Intel-based chip and a Toshiba A70, with an ATI mobile 9600.  So it's a good guess it's a driver quirk right in X, probably the part that handles extended displays.  I can get either device to display video without issue (aside from crappy resolution) in mirrored display.

I've just been testing with the mini 9, and can successfully configure extended video display to the highest resolution Ubuntu (and Linux Mint) can display by autoconfiguration on an external 17" display.  I'll play some more with my Sharp 52" TV later on at home, but the simple solution is as follows:

Go into Monitors setting applet.  Unmirror the displays.  Drag the external display rectangle above the internal display and set it to whatever the highest available resolution is (or in my case a 16:9 that I like).  Hit Apply and enjoy video playback.  So far has been working very consistently, but this is only one netbook.  I will try with the "big guy" later, and output to the 52" at a 16:9 resolution there, too.

---

### Post by P_Squiddy on 2010-06-17
Tested more with the Dell mini 9 on my 52" Sharp and sure enough, putting the external display on top works beautifully!  Didn't haul out the old Toshiba A70, but I'm willing to bet it will work.  I'll post one final follow-up on this as soon as I get the chance.  Now, is there one bug filed against this issue that I can provide feedback to as well?  Looks like this should be fixed across the board.

---

### Post by cmuxed on 2010-08-08
> Now, is there one bug filed against this issue that I can provide feedback to as well?[B]
@P_Squiddy[/B]
I didn't fill out a bug, but I'll take a look and log one if there isn't.  Watch this space :)

---

### Post by cmuxed on 2010-08-08
A bug has been logged for this issue: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/614921](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/614921)

See this great article on how to use xrandr in a start up script; you can use my original commands in conjunction with the startup script to automatically set up your screens at boot... a viable workaround until the developers can fix this permanently!  [https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor](https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor)

Cheers! :)

---

### Post by cmuxed on 2010-08-09
Just to keep you in the loop, I received an email today confirming this is a bug

> 
** Changed in: xorg-server (Ubuntu)
       Status: New => Confirmed

-- 
Video playback blank at 1900 x 1200 resolution
[https://bugs.launchpad.net/bugs/614921](https://bugs.launchpad.net/bugs/614921)
You received this bug notification because you are a direct subscriber
of the bug.

Status in “xorg-server” package in Ubuntu: Confirmed

Bug description:
Binary package hint: xorg

When playing a video, the screen is blank.  I need to turn off my extended desktop and turn it back on with the xrandr command.  I have a thread on the forums open with others vouching for this same issue.  I have recently moved to a fresh install from Karmic to Lucid and the problem remains.

[http://ubuntuforums.org/showthread.php?t=1440142](http://ubuntuforums.org/showthread.php?t=1440142)


---

