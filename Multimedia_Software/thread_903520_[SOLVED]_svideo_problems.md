---
title: "[SOLVED] svideo problems"
date: 2008-08-28
forum: Multimedia Software
---

### Post by erutufon on 2008-08-28
I have been fighting my pc to get the svideo output to work, so I can watch films on my TV. I am using an ATI radeon 7000 graphics card, with ubuntu 8.04.

from a fresh install, the graphics card drivers seemed to be working (I got the extra visual effects working).  However there was no output to the TV.
I tried the method here (HOWTO: TV-out for legacy ATI cards using GATOS)
([http://ubuntuforums.org/showthread.php?t=215763&highlight=radeon+7000+svideo](http://ubuntuforums.org/showthread.php?t=215763&highlight=radeon+7000+svideo)). 
no luck with that - anyone have any idea how i can solve this?
many (times many) thanks in advance

---

### Post by djRobbieF on 2008-08-28
Just a shot in the dark, but when you booted your computer, is the s-video device (your projector or TV) connected to the s-video on your ATI card, and powered on?  If it's not detected, it won't be an option.

Also, if on a laptop, is your s-video activated with the appropriate FN key?

---

### Post by CarpKing on 2008-08-28
IIRC, GATOS is no longer supported.  You should try XRandR: [http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)

[http://ubuntuforums.org/showthread.php?p=5682327](http://ubuntuforums.org/showthread.php?p=5682327)

---

### Post by erutufon on 2008-09-03
have been trying to solve this problem for a while now, and have tried using the advice on the wiki and the ati drivers page.  I had no luck - seemed to run into errors on the wiki page, and my skills at terminal are pretty low as I'm a noob.

the aim was to get a "media pc", which would plug into the tv via the svideo, so that (legally downloaded) films could be watched without burning to disk, as well as internet on the tv etc.  

So after a fair amount of faffing, I got the computer to spit out a tv out through the svideo, but only if the pc was in low graphics mode.  I achieved this by going through each radeon driver in turn, testing it out and hoping it would work.  one of them did, but with low graphics mode the monitor looked crap.  So i thought I would tweak it, to sort it out.  I broke it (foolish).  after a fresh install, I couldn't get it to work at all, and was mightily pissed off.  In frustration, i thought to try another distro, and put a Freespire disk into the cd drive and booted it up.  this worked first time, pretty much.  I had to change the graphics drivers to VESA, which I could do on the set up screen as I was installing.  Within half an hour, i could watch computer output on the tv.

If anyone else has the same problem (radeon 7000, can't get the tv output to work), then i recommend trying freespire.  I am still using ubuntu on another pc, because I like it, understand it (a bit) and it's good. but for this application, it seems like freespire is simply a lot easier to set up, particularly for a noob.  As for freespire itself, it seems a bit strange and clunky after ubuntu, but I think as i get used to it, it should be fine.:)

---

