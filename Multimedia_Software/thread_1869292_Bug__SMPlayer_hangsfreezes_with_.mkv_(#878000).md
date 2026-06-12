---
title: "Bug:  SMPlayer hangs/freezes with .mkv (#878000)"
date: 2011-10-25
forum: Multimedia Software
---

### Post by drawkcab on 2011-10-25
So SMPlayer is freezing whenever I use it to play HD .mkv files via vdpau. (see below)  Unlike the bug report, however, I am using Gnome shell.

Is anyone else experiencing this bug?  Has anyone found a workaround?  

[https://bugs.launchpad.net/ubuntu/+source/smplayer/+bug/878000](https://bugs.launchpad.net/ubuntu/+source/smplayer/+bug/878000)

> Release: KUbuntu 11.10
smplayer version: 0.6.9-4

Smplayer is basically unusable in the new ubuntu release. When I try to play anything with it, it hangs and its GUI does not respond to any events (mouse click/move, keyboard commands). It can be only killed. However, it seems that mplayer itself is working, i.e. it plays the movie, but this process is out of any control, I can only wait until the end of the movie. Mplayer also works normally when starting it independently from the command line. When the movie is ended, mplayer stops playing, but smplayer continues to hang until killed.

---

### Post by drawkcab on 2011-10-26
Wow.  I can't believe no one else is having this problem.  I've reinstalled 11.10 to get the exact same problem.  Letting smplayer run eventually freezes the entire desktop!!

---

### Post by beew on 2011-10-26
I have no idea what happens, but it seems that SMplayer has stopped developing at some point,--I stand corrected if I am wrong on this,-- you may want to try umplayer and see if you have better luck, it is a fork of Smplayer so it is very similar except it has more features.

[http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html](http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html)

BTW, how do you know it is a SMplayer problem and not a problem in the mplayer backend? Have you tested with other mplayer front ends like gnome-mplayer or using mplayer with the command line to make sure that it is not a mplayer problem?

---

### Post by drawkcab on 2011-10-26
> **beew said:**
> I have no idea what happens, but it seems that SMplayer has stopped developing at some point,--I stand corrected if I am wrong on this,-- you may want to try umplayer and see if you have better luck, it is a fork of Smplayer so it is very similar except it has more features.

[http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html](http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html)

Thanks for the suggestion.  I already gave up on Oneiric and reinstalled Natty on my HTPC.  Even so, I'll keep working on the problem on my laptop.

> **beew said:**
> BTW, how do you know it is a SMplayer problem and not a problem in the mplayer backend? Have you tested with other mplayer front ends like gnome-mplayer or using mplayer with the command line to make sure that it is not a mplayer problem?

I honestly don't know because I've never been able to get mplayer to play HD .mkv without the smplayer front end.  Here's what I know:

Standard def runs fine on both.
Smplayer worked fine with HD .mkv in Natty.
Smplayer worked fine with HD .mkv in Oneiric last week before the major update.

The thing that leads me to suspect smplayer is the fact that 1. the movies plays 2. the gui freezes until, finally 3. the desktop freezes.

If umplayer works in Oneiric, then I'll not think about it too much and just move forward.

---

### Post by drawkcab on 2011-10-28
Found out that the bug involves the cache.  Set the cache to zero and everything's fine again.

---

### Post by andrew.46 on 2011-10-29
> **drawkcab said:**
> Found out that the bug involves the cache.  Set the cache to zero and everything's fine again.

I have heard of this problem with UMPlayer as well. Can you confirm the setting you altered? I attach a screenshot...

---

### Post by drawkcab on 2011-10-29
Yeah, set those to zero.

---

