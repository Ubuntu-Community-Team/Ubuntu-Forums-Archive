---
title: "Upgrade to 9.04 Breaks IVTV Tuners (PVR-500)"
date: 2009-06-10
forum: Mythbuntu
---

### Post by tduffy83 on 2009-06-10
While watching tv in mythtv the picture skips around erratically, totally unwatchable.  Recordings are the same.  

This has been replicated on two different machines, with different video cards, both were first upgraded, then fresh installed, and the same problem happens every time.  Also upgraded to mercurial v4l-dvb via compile and the issue remains.

They were working perfectly under 8.10.  I think something in 9.04 has broken IVTV cards (PVR-150, PVR-500, etc).

I would just reinstall 8.10 but I need the newer intel graphics driver to enable TV-Out and I can't seem to install this driver on 8.10, only 9.04.

Motherboard is DG945LF2, Dual Core intel Atom, GMA 950 Graphics, 2GB RAM.

Other machine is older P4 2.8GHz with Radeon 2600HD and 2GB Ram.

Any help would be appreciated, the Atom machine is going to be a birthday gift and said birthday is coming up!

---

### Post by tduffy83 on 2009-06-10
Update:  The issue does appear to be IVTV related as opening the tuner in VLC gives the same result.  

I do not believe this is a signal issue as my TV does not have this issue when plugged into the same coax cable.  I will try to clean up the signal and see if it helps and post back.  Meanwhile suggestions would be welcome.

Edit:  Can't be a signal issue because as I said before, 8.10 works flawlessly.

Back to the drawing board.

---

### Post by superm1 on 2009-06-10
Can you try an 8.10 kernel?  That's where IVTV comes from..

---

### Post by tduffy83 on 2009-06-10
I'm afraid I do not have enough Ubuntu savvy to know how to downgrade to a 8.10 kernel.  Help would be appreciated.

---

### Post by superm1 on 2009-06-10
So hopefully you should still have an 8.10 kernel installed.  From the grub boot menu see if it's there.  If not, then look and see if you can install it from synaptic.  You might be able to.

---

### Post by tduffy83 on 2009-06-10
Well at this point I've installed a fresh copy of 9.04 so I don't think the 8.10 kernel is still there.  I'm going to be installing 8.10 again so that I can copy the IVTV firmware from the working setup and also figure out the kernel version that I had working before.  These two things (kernel which has the driver, and firmware) are the driving forces behind getting this card to work.  

Maybe the 9.04 kernel broke IVTV or uses bad firmware.

I'll post back on my progress later.  If this isn't a driver issue I'm afraid I will not know where to go.

---

### Post by ian dobson on 2009-06-11
Hi,

I've been seeing problems with my PVR-500 for the last few kernel updates (8.10). I ended up solving the problem by manually installing the bleeding edge drivers.

See [http://ubuntuforums.org/showthread.php?t=968121&highlight=pvr+500](http://ubuntuforums.org/showthread.php?t=968121&highlight=pvr+500) for my solution.

Regards
Ian Dobson

---

### Post by tduffy83 on 2009-06-11
I already installed the bleeding edge linuxtv drivers (which include IVTV) and that did not work.  BTW later kernel updates in 8.10 fixed the PVR-500 IVTV issue, and I've never had a problem with 8.10 and my PVR-500.

Using the kernel from 8.10 and the 8.10 firmware did not work either.

This all leads me to believe that IVTV is not the problem.

I am truly at a loss.

---

### Post by tduffy83 on 2009-06-11
Ian,

Are you currently running 9.04 with no problems?  If so what version of the tuner do you have?

Is anyone else having this problem with 9.04?  I don't see how I could be alone as all 3 of my PVR-500 cards have this problem across multiple machines.  

I think mythbuntu users get their machine working and then live in fear of upgrading because inevitably it will break something.  That's the only thing I dislike about Ubuntu and is a problem I've noticed with a multitude of hardware not just TV Tuners.

---

### Post by ian dobson on 2009-06-11
Hi tduffy83,

No I'm staying with 8.10 due too all the problems I've heard about with 9.4. I usually wait 1 or 2 months before upgrading anyway. And as my backend is running well at the moment I've got no need to update.

Regards
Ian Dobson

---

### Post by tduffy83 on 2009-06-11
I've found a very dirty workaround that seems to be working for now.

First I installed 8.10 and updated it to current 8.10 repos.

Then I added the Jaunty repository to sources.list and the Intel driver repo.

A simple sudo apt-get install xserver-xorg upgrades the xserver and pulls in the shiny Intel video driver with it.

This enables the s-video tv-out functionality of the motherboard, yet leaves me with all the other 8.10 packages which are needed to get the pvr-500 to work.

I am shocked this worked, I thought it would break.  I guess this will do for now.

I'd rather use a fresh install of 9.04 so heres hoping this is fixed in a later kernel update.  Should I post a bug report?

---

### Post by Bartth on 2010-04-29
I first came to this post when I experienced the same problems, and bookmarked the post for later reference.  

Since I've finally been able to resolve my issue, I thought I'd post back on this post where my google search first brought me. 

My fix was changing the image size in the recording profiles. 

I've posted, what worked for me, on the bugpage: [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/550173](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/550173)

---

