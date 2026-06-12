---
title: "[SOLVED] HELP!! I never thought configuring a mouse would screw up my video card"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by jai_mantravadi on 2007-11-13
Ok, now I'm *really* pissed. Not obviously at anyone in the OS community (because all those developers work on their own time), not at anyone on the Ubuntu Dev team (because they make an excellent operating system), however I'm (I think reasonably) pissed that I can't get something to work, that should work based on community documentation, and now I broke something that shouldn't even have broken. 
The story goes something like this
1) Can't get direct rendering to work either open-source or ATI driver (running Kubuntu 64 Feisty/Gutsy, athlon 3200+, ATI Radeon 9800 Pro) (See [here]("http://ubuntuforums.org/showthread.php?t=560066") or [here]("http://ubuntuforums.org/showthread.php?t=579658"))
2) I'm settling (read: finally giving up) for 2d desktop with the radeon (open source) driver because that at least gets me pretty decent video for multimedia (movies/video, etc).
3) Then I decide to apply those excellent instructions for finally getting all those extra mouse buttons working using the instructions [here]("http://ubuntuforums.org/showthread.php?t=332256")
4) ctrl-alt-backspace and bob's your uncle, it works (sorta)... So, I figure a re-boot is better than just restarting xserver and...
5) Terminal login!!! Yipes, copy that xorg.conf back over, reboot and...
6) Terminal login!!! Repeat 5 (just kidding... well, not after trying a few other good xorg.confs)
7) So, I look through dmesg, Xorg.0.log, and I can only find that the ati/radeon driver IS NO LONGER WORKING!!! It says "Screen found, but no valid modes" hmmm...
8) try a good-old sudo dpkg-reconfigure xserver-xorg, tried the trusty old defauls - no dice, tried the settings that I *know* worked before... no dice
9) 	](*,) :confused: :mad:
10) I tried the vesa driver, and it works, but... this is *less* than ideal
11) I did delete the "rules" file listed in the mouse instructions, but that has had no effect on getting

There may be a bit more to the story in that I just purchased a widescreen monitor, but it was working before step 3. It was basically shutdown, plug in, reboot and it worked. Best of all, Ubuntu selected the native monitor resolution! I was so happy when it was working, but now I'm really frustrated. I've tried the xorg.confs from when it was working (which were the exact same as my other monitor, except with a slightly different resolution listed)
I really would've liked to do this without a reload... In fact, I was hoping to upgrade hardware without a reload ([like this]("http://ubuntuforums.org/showthread.php?t=544451")). 

Any suggestions?
Attached are my 3 latest xorg.conf files, the "xorg.conf" is the one using vesa drivers, the ".works" files are bakups from before I tinkered with the file, the one from november is with the widescreen monitor working, and the one from october is with my previous monitor (but it worked with my widescreen monitor at a lower resolution).

---

### Post by NT4usB on 2007-11-13
No answers... couple ideas.
I'm looking at your xorgs and see some screwy entries (bus id twice, buncha options I don't understand, etc)  in the Device section. 
Xorg.log should be showing a bunch of (WW) on stuff that's not loading and being skipped. Comment those out of the xorg.
Vf looks high... 130?

Since I'm a big envy fan, I'd grab that and use it to remove everything ATi. Then (I would) use it to install the driver, or you could install via the restricted package mangler. You'd be working from a terminal or change the driver to vesa to get a gui to run the pkg mgr.

I dunno... went through similar on a box last night. Previously working nic wasn't working after swapping some hardware around. Resource conflict or ?
Went to swap it around to another slot and found it wasn't seated... &$%@ will drive you nuts sometimes...

---

### Post by jai_mantravadi on 2007-11-13
I'll try dropping the VF (VF too low can't hurt, right). As for the other options, all of them load (no WW on those options from Xorg.0.log). Most of them are holdovers from when I was trying to get DRI/AIGLX to work under Feisty with the open source radeon driver. Basically commenting them out doesn't hurt or help . Anybody else have other ideas?

---

### Post by jai_mantravadi on 2007-11-15
Bump... I'm also a little frustrated that my threads seem to get 1 reply, and then no more posts. Am I posting something wrong? I typically try to respond in a timely manner to those that help out, but end up having to give up because I don't have enough experience with linux to fully debug my problems, and after a few posts, it seems others give up.

---

### Post by chiefbearclaw on 2007-11-15
Its easy as hell to give up when you mention ATI... :lol: I just scanned your post and have not looked at your xorg.conf's but I can say that resolution and refresh rates may be a factor. If you read any of my posts in other areas of the forums you will see that my advice results in shooting yourself in the head and reinstalling the ati driver again in the afterlife. I haven't gone 72 hours without reinstalling my Linux OS. (Dual booting XP pro and LinuxMint XFCE). I could care less about getting all my mouse buttons to work. I just want my ati card to work with some build of 7.10. G'luck and I'm sure someone will reply with helpful advice... just have to be patient.

---

### Post by jai_mantravadi on 2007-11-15
Thanks for the advice, and sorry for the frustration. I just see that if these go a few days without being bumped or replied to, they don't typically get read. I'm probably going to  re-install and then we'll see if everything works. Oh, and by the way, I'm talking about the OPEN SOURCE ATI driver, (never even got fglrx working). I was hoping with ATI opening up the specs that we'd see a better open-source driver, but I guess they're still working through the full details of what that means.
Jai

---

### Post by NT4usB on 2007-11-15
So, some of us get a little frustrated when we post suggestions and don't see any indication that they were ever tried? 
Did you ever try my suggestion of using envy to completely remove the ATi stuff?
If so, a simple btdt would be nice so I can unflag this thread and remove it from the 200 or so I'm watching and trying to help with.

Reinstalling is only going to work if you get the rendering to work first time you try. Otherwise, your system is going to get cluttered up, just like it is now, making other attempts to get it working.

In all three of your threads you tried envy.
Which version did you use? Last time I had trouble with it, I was using one I downloaded a couple weeks before to install on another (9600 Pro) machine. 
Stingy me, trying to save some bandwidth and not download it again. Grabbed the latest and it worked fine.
Anyway, short story long...

Have you looked at this? [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

ed: I'm guessing you didn't have the latest since there was a new stable release on 12 November.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by jai_mantravadi on 2007-11-16
Mea culpa! Indeed, I have not tried the latest envy release. I guess I had given up on the closed-source driver and was looking only at the open source driver. Also, is there any reason for the open-source driver to break configuring the mouse? I'll get on this and try things again with the latest Envy build and updated wiki (for gutsy) and post back. Thanks!
Jai

---

### Post by jai_mantravadi on 2007-11-17
First tried envy... again no dice (I got my happy black screen staring back at me). The computer thinks its displaying, but nothing shows up on the monitor. So... I tried the manual install instructions on the wiki, re-installing the mesa drivers in-between just to be safe. After a bit of finagling, I finally got the 64-bit package put together (not quite as direct as the wiki states), and again rebooted to a completely blank screen. Please note, Ubuntu's splash screen shows when booting up, but not the login screen. It is directly due to the ATI closed-source driver because the vesa driver (and at one time the open-source driver) works. 

Seriously, at this point I'm just curious why the open-source driver all-of-a sudden failed to load when I was changing things in the mouse section of the xorg.conf.

As far as graphics go, I'm going to reload once (to attempt to see if the auto-detection/3-D effects will work), and then I'm upgrading my mobo/graphics card (had this planned for a while, but was waiting on all hardware to be shipped).

I'll be moving to an on-board radeon X1250. I'll post back to all these threads if open/closed-source drivers work with the new system.

---

### Post by jai_mantravadi on 2007-11-23
OK... now that I've tried a fresh install off the gutsy DVD (took a couple of coasters to figure out my CD media was a bad batch), Direct rendering was working with the open-source driver out-of-the box. Compi Fusion took about 2 minutes to install, and even less time to get working. Haven't tried fglrx yet, but I'm not sure that's worth it since I'm upgrading the hardware in a few days :). Thanks to everyone who tried to help me get the [open and closed source] drivers working. Sorry for the frustration. I never did figure out why direct rendering wasn't working, (or how installing a new mouse driver can screw up a graphics card even after reversing the instructions completely).
Jai

---

