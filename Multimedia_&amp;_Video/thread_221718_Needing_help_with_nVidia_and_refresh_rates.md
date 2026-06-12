---
title: "Needing help with nVidia and refresh rates"
date: 2006-07-23
forum: Multimedia &amp; Video
---

### Post by zami on 2006-07-23
Hello all.

I seriously need some help (okay I'm asking for outright hand holding here!) with getting my refresh rate up.

I've got a nVidia GeForce 6800 GT video card, and a NEC MultiSync FE700+ monitor.  And a refresh rate locked in at 60hz.

The monitor is strobbing, and reading like this is EXTREMLY difficult and painfull.

I'll list below what I've tried so far.  

**Tactic1**
This document ...
[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#graphics-cards](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#graphics-cards)
told me to
*glxinfo | grep rendering*
The result was *direct rendering: no*

Then I followed the next directions...
“..if you have a newer card, install the nvidia-glx package from the Restricted repository..”
and TRIED to add all the restricted repositories... hell I tried adding them all, but the connection times out at file 12of15.

Regardless of the above failure,  and with fingers crossed, I then followed the next set of instructions and 
*sudo nvidia-glx-config enable* 
and get the result *command not found*.

**Tactic2**
I've tried downloading anything and everything at nVidia that has even a remote chance of pertaining to me, from
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
hehehe... yeah, I don't even know what to do with these files so again I've tried about anything I can think of with the predictable results of nothing happening!

I'd really appreciate ANY help in this.  This is day one as a Linux user for me, and I am THRILLED with it so far.  It feels... quick! Unfortunetly I can't look at my monitor for more then a few minutes wich is a real potential deal breaker!

Thanks all!
-zami

PS I have searched the forums but I've only found references to dealing with glx on Breezy (?), or nVidia stuff relating to the TV setup.  But if there is a handy post I've missed I'd appreciate a good shove in that direction.  :D

---

### Post by jay_cee on 2006-07-24
If you can't get help here, try to nvidia linux forums:

[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

That's where the real experts hang out.

---

### Post by Neobuntu on 2006-07-24
NEC MultiSync FE700+ :
----------------------
Horizontal frequency: 31 - 70 KHz
Vertical frequency: 55 - 120 Hz

I looked it up for you (according to the specs from a amazon.com sale.)

Cut and paste the following:

    sudo dpkg-reconfigure xserver-xorg

Select the defaults (save maybe the Nvidia module instead of "nv.")

Toward the end, select ADVANCED monitor set-up and put these figures (above) in.

That will take care of the best resolution AND refresh rate that your monitor can do. If you want a lesser res (like 1024x786,) just (before the advanced selection) uncheck the higher resolution(s), you never want to see(during the reconfigure.) If you don't, your login screen will always be at the highest res and you might not like the tiny login. 

Hope that helps, is what you need and fixes it QUICKLY.

P.S. Now the Display settings in KDE or Gnome will let you lower the refresh rate as you please.

This kind of thing might not be auto-magically preset-up because it could damage older and less capable monitors.

P.S.S Yep, you may not like 1280x1024 at 66 on that screen but 1024x768 at 85 will look nice with your .24 dot pitch. Don't envy flat panel screens too much because you probably have better blacks and better movement with direct 3D (DRI.) 

Oh! sudo apt-get install torcs
Nvidia preferred!

If you're still using nv, you need to install the Nvidia driver (I think it will even update with the new processor kernels for you. It's Thier called "restricted" modules. You shouldn't have to load the "legacy" ones after kernel auto upgrades. Your Nvidia isn't legacy.) 

I suggest simply looking up (here) and installing Automatix, run it and checking the Nvidia box and let it fly. Now you should have direct to graphics card rendering(DRI.)

---

### Post by tseliot on 2006-07-24
Read my guide (to install the driver) and its Problems Section (for the Refresh Rate)

[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by zami on 2006-07-24
Thank you!!

Much thanks to you each.

Jay_cee, I've bookmarked the nvneiws forums just in case.

Tseliot, I'll go through your guide in a moment and I'm sorry if I missed it in a forums search before.  I appreciate the friendly link to it!

Neobuntu, THANK YOU for the walkthrough for the monitor setup.  I'll tackle my video card in a few minutes here, but the main goal is achevied.  My monitor display is now still as stone, and a lovely 1024x768.  Aaahhh...

Honestly, I don't think I'd have found that step-by-step setup (xorg?) on my own.  I'm at that awkward tongue-twisting stage of learning where I don't know enough, to know if I'm even asking the right questions.

I'm doing
sudo apt-get install torcs
now and heading to read the driver guide.  I'll post when I get an outcome.

Whew! Let me say, this is great.  I can actually read the help documents and forums now, and actually learn something from them instead of just feeling confused and queesy.  Sorry to ramble... but WOW, what a huge releif this is.

-zami

---

### Post by cracker on 2006-07-24
> **zami said:**
> ....I tried adding them all, but the connection times out at file 12of15.

I recently installed Dapper on a machine, and found that most of the repositories timed out. After some fiddling, I discovered that changing all references to

us.archive.ubuntu.com

to

archive.ubuntu.com

fixed everything. Possibly some messed up DNS, possibly a permanent change, but either way, it works now.

---

### Post by Neobuntu on 2006-07-26
You are welcome ubuntu friend. I'm glad it fixed the flicker for you. There were many ways to do that and I hope my way was faster for you (TIME saving IS ease of use for geek and newbie alike.) I should have said that one can just about hold down the <Enter> key through most of the xserver reconfigure. Some may find they prefer editing the "xorg.conf" file.

Did you load up Automatix and select Nvidia (direct 3D) DRI driver before TORCS (The Open Source Racing Car Simulator?)

One could skip Automatix and just add the Nvidia DRI drivers via the Ubuntu Wiki. Automatix is good for MANY things.

I just got an ATI 9600 card working (DRI) with TORCS in a Gateway laptop. Cool but remember, right now, always buy Nvidia.

---

