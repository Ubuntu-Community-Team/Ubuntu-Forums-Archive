---
title: "Still no love for CRT monitors?"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Tricore on 2007-05-07
Hello there!

I've been with Linux on a kinda very unstable relationship for several years yet, and I don't really consider myself a noob anymore (probably ever since I installed Gentoo, and realized it wasn't all that hard).

Now, I really like the way that Ubuntu is doing, in a **lot** of ways it is actually MORE user friendly than Windows XP. This is except for one small thing; with every single linux distrobution I've **ever** tried (and that's quite a few), I have never tried where CRT Monitors worked out of the box - and Ubuntu is no better. I always start out with just a few resolutions at 60hz. In the case of Ubuntu 7.04 I get to choose between 640x480@50hz or 800x600@50hz, and this is not even enough to see the entire installation window and finish the installation!

The solution to this problem is rather simple for me, but it isn't for everybody. I'm getting quite used to opening terminal and writing those "sudo gedit /etc/X11/xorg.conf" and then putting in the right values for Horizontal and Vertical refresh rate, and as I always forget where to put them fire up another terminal and go "man xorg.conf". But I just can't understand the need to go through all of this hazzle, when Ubuntu knows how to automatically get Compiz working with just the click of a button!

Maybe it's just my monitor, and I realize that this issue is becoming less important as people are beginning to use TFT monitors. But still, a lot of people are using CRT's and I just find it wierd that the first thing a newbie would have to do, in order to install the most user friendly version of Linux ever, would require him or her to know some quite bizarre technical data about ones monitor and from terminal (or GUI, but that's not easier at all IMHO), write this information to another wierd configuration file.

Is it really so hard to make it work out-of-the-box ?

---

### Post by tanelt on 2007-05-23
I have the exact same question!


If I didn't have to go through all the trouble over the years just to get it working properly, I'd probably be contributing a lot of artwork/code/translations/etc to Ubuntu by now.
But I guess I'm unable to do that for many more years. =\

---

### Post by BobLand on 2007-05-23
When I first installed Ubuntu the highest resolution was 1024x7xx.  I have an old Viewsonic P815 21" CRT. I could not get 1600x1200.  I spent days on it and finally gave up and went back to Windows 2000.  Eventually, the lure of Linux got the best of me and I tried again.

One thing I did was go up to the Viewsonic site and got the configuration for this monitor for the xorg.conf.  No difference.  No change.

Once I ran the coorect driver from nVidia, the driver changed xorg.conf adjusting the monitor and video card specs.  After rebooting, the monitor displayed the proper 1600x1200 and has been stable ever since.

My video card is a GeForce4 xxxxxx(can't remember the exact details).  I used the nVidia legacy drivers.

Video has been somewhat of a problem for Ubuntu but, for me, the problem was in the correct video driver and how you install it.  I installed just about every driver possible until I got the correct driver/installation sequence.

It's a pain but hang in these.  It will work.
Bobland

---

### Post by eye208 on 2007-05-23
> **Tricore said:**
> I always start out with just a few resolutions at 60hz. In the case of Ubuntu 7.04 I get to choose between 640x480@50hz or 800x600@50hz, and this is not even enough to see the entire installation window and finish the installation!
It seems there is a problem with the DDC connection between video card and monitor so that Ubuntu is unable to read the specs of your monitor. In this case, 640x480 or 800x600 at 60Hz are the only safe options. The same thing will happen if you install Windows on a system whose video card is not supported out of the box.

Until Ubuntu 7.04 I had the exact opposite problem: My 15inch TFT supports 1024x768 max. and Ubuntu's LiveCD mode always ran into "out of range" errors with the default driver because it would be configured to 1280x1024 by default. I had to Alt+F1 onto the command line, edit xorg.conf, Alt+F7 back to X and then type Ctrl+Alt+Backspace to restart X and get a working display. The safe mode option of Ubuntu 7.04 for the first time recognized my display specs properly.

---

### Post by Shazaam on 2007-05-23
The problem I have with ANY flavor of Linux and my crt is that the desktop changes position on EVERY boot. Sometimes it will be offset to the left, sometimes to the right. I have used default lines, custom lines, used "generic monitor", Viewsonic, etc and changed the position with the monitors OSD. It does the same thing if I use the generic or the nvivia drivers.  With Windows all I have to do is set it once and it would stay that way forever if I didnt have to keep futzing with it in Linux.:D

---

### Post by itsjustarumour on 2007-05-23
> **Tricore said:**
> Hello there!

I've been with Linux on a kinda very unstable relationship for several years yet, and I don't really consider myself a noob anymore (probably ever since I installed Gentoo, and realized it wasn't all that hard).

Now, I really like the way that Ubuntu is doing, in a **lot** of ways it is actually MORE user friendly than Windows XP. This is except for one small thing; with every single linux distrobution I've **ever** tried (and that's quite a few), I have never tried where CRT Monitors worked out of the box - and Ubuntu is no better. I always start out with just a few resolutions at 60hz. In the case of Ubuntu 7.04 I get to choose between 640x480@50hz or 800x600@50hz, and this is not even enough to see the entire installation window and finish the installation!

The solution to this problem is rather simple for me, but it isn't for everybody. I'm getting quite used to opening terminal and writing those "sudo gedit /etc/X11/xorg.conf" and then putting in the right values for Horizontal and Vertical refresh rate, and as I always forget where to put them fire up another terminal and go "man xorg.conf". But I just can't understand the need to go through all of this hazzle, when Ubuntu knows how to automatically get Compiz working with just the click of a button!

Maybe it's just my monitor, and I realize that this issue is becoming less important as people are beginning to use TFT monitors. But still, a lot of people are using CRT's and I just find it wierd that the first thing a newbie would have to do, in order to install the most user friendly version of Linux ever, would require him or her to know some quite bizarre technical data about ones monitor and from terminal (or GUI, but that's not easier at all IMHO), write this information to another wierd configuration file.

Is it really so hard to make it work out-of-the-box ?

For what its worth, I've tried many distros and when recognising/configuring CRT monitors openSUSE has always been way, way ahead in this (I've used 4-5 year old CTX and Iliyama 19" monitors)  

For instance, case in point with my current monitor -  Ubuntu recognises it as a "Generic 19" monitor" with maximum refresh rate of 52Hz and maximum resolution of 1024x768.  openSUSE gets it exactly right as a "CTX PRF960F 19" CRT Monitor" with maximum refresh rate of 103Hz and a full range of resolutions up to 1600x1200.

Come on Ubuntu, I think theres still a bit of work to be done in this area!

---

### Post by Tricore on 2007-05-23
Hey, thanks for replying! :D

Well Ubuntu should be able to give me 1280x960@85hz - Windows is. Even if Windows doesn't recognize my monitor as anything other than "Analog Monitor".

As to what distro does this better than others... well, the only distro that worked right outta the box for me was Gentoo, but then again, it didn't configure xorg.conf automatically ;-) I remember back in the days of Red Hat / Fedora Core 1 when I actually ran a guide that ASKED me to select my monitor from a list (it was there!) and it still didn't work! :S

---

