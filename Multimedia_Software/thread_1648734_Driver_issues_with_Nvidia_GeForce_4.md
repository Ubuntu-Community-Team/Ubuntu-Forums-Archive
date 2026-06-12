---
title: "Driver issues with Nvidia GeForce 4"
date: 2010-12-19
forum: Multimedia Software
---

### Post by jord1981 on 2010-12-19
I recently upgraded to 10.10 (from 08.04).  I have an old GeForce 4 MX4000 video card.

I was using the proprietary drivers previously.  Throughout the upgrades to each version, things seemed to be working well but when I hit 10.10 I got some issues.  Originally the display looked ok but lagged when playing video.  I ran nvidia-xconfig and the result was a loss of the GUI.  I played around with xorg.conf and eventually just deleted it which gave me pretty good video actually and went with that for a week or so.

Yesterday, I was trying to get my second display working (I have a 50" tv connected by VGA cable and then a smaller TV in another room connected by s-video which I use just for video playback).  This has always worked for me on Windows and with 08.04 on this system but had not been working since the upgrade to 10.10.

I tried the proprietary drivers nvidia-173 and nvidia-96 and the community's nv.  None worked well, some not at all.  After giving up, I tried to go back to where I was.  I removed the new drivers I had downloaded and deleted xorg.conf.  However, now I am stuck in a low-resolution 4:3 video mode with no option to change it.

I've searched around and it seems that there are some compatibility issues in 10.10 with older Nvidia cards, so I am guessing this is probably the root of my problem.

I am hoping that you may be able to help me: 1) get full resolution back on my 50" connected by VGA, and as a bonus 2) get a cloned view working via S-Video.

Many, many thanks in advance.

---

### Post by theasprint on 2010-12-19
Hi, I have experience solving Nvidia graphics problems in Ubuntu.

For better guidance, I think you should go to the thread in my signature (not the bootinfoscript link).

In that thread, there is a user named RawGod whose instructions are good enough to follow.

Summary of steps is to
1. Start afresh (not meaning to reinstall, just disable nouveau and do  not use Nvidia drivers provided by Ubuntu, the proprietary ones in  hardware drivers.)

2. Then go to Nvidia's website and get the driver for your Nvidia card. (get the linux version)

3. Turn off gdm by executing
```
sudo /etc/init.d/gdm stop
```

4. Install drivers by executing
```
sudo bash <your Nvidia Driver's directory>
```

5. Start gdm again.
```
sudo /etc/init.d/gdm start
```

Good Luck:D

---

### Post by jord1981 on 2010-12-19
Worked like a charm - many thanks!

---

### Post by theasprint on 2010-12-20
Hi, 

Happy to know that your problem is solved.

I would just like to tell you to mark this thread as solved (under thread tools, if I'm not wrong)

Enjoy your HD Ubuntu!

---

