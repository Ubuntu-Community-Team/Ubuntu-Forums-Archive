---
title: "Video Tearing Problem Fixed with DPMS ???  What !?"
date: 2008-04-30
forum: Multimedia Software
---

### Post by arsenic23 on 2008-04-30
Ok I'm hoping someone can shed some light on this for me.  I recently built myself a new Quadcore machine to replace my aging 3000+ and I went ahead and got a 2009w lcd screen from Dell while I was at it.  My monitor got here first so I used it on my old machine, after tweaking xorg.conf, while I waited for the rest of my parts to get here.  It worked perfectly.


Tonight I thought I'd let some steam off and watch Gunbuster on my new PC, but to my great surprise there was terrible video tearing on any high action - high contrast scene.  I messed with the usual suspects like *nvidia-settings* and whatnot, but after many many restarts of X my video was still 'the suck'. 

So I brought up the xorg.conf from my old rig and started looking through it too see if my monitor was setup correctly, I was thinking that maybe I needed to set the refresh or something.  But my old xorg didn't have any option in the monitor setup at all, save for DPMS.

I turned it on, even though I was under the impression that it was only a power saving option, and low and behold I have no tearing while playing video files now.....  That makes no sense to me at all.

Can anyone shed some light on this for me?  Does DPMS do something I don't know about ?

---

### Post by arsenic23 on 2008-05-09
lol - Now I feel stupid.

Turns out that the problem was with a Compiz setting the entire time.  When I rebooted the gui that last time Compiz failed to load and so it looked like adding DPMS fixed the problem.  Turns out Compiz needs to be set to vsync independantly of the Nvidia driver.


-------------------EDIT:
Can I not mark threads as solved anymore ?

---

