---
title: "How to control Pandora, via Prism, with remote?"
date: 2008-04-21
forum: Mythbuntu
---

### Post by sceo on 2008-04-21
I have downloaded the Linux version of Prism onto my Mythbuntu box, and have created a "prism app" for Pandora (after installing Adobe Flash Player via Firefox).  I then created a menu item for "Listen to Pandora" under the media library, so the Prism app opens up, still has me logged in, and starts playing.  Brilliant!  When I quit, the frontend gets focus back.

Now, Pandora allows some keypresses for partial control (play/pause with spacebar, + and - for thumbs up/down, etc).  How can I get my remote control to map to these for Prism (which is basically Firefox with some toolbars and stuff stripped out)?  That is, I want to "thumbs-up" a song in Pandora by hitting the "UP" key on my remote.

Is this possible?

---

### Post by laga on 2008-04-21
Try 'irxevent', you can use that to send X events with your remote control. I hope that the frontend won't be interpretting your remote buttons when your app is running, though.

Can you elaborate a bit on Pandora? Sounds interesting.

---

### Post by Visti on 2008-04-21
Well, I guess you could point the shortcut to a script that opens Pandora after remapping the keys for the needed functions using xmodmap and then, when closed, maps it back again. It's an easy, but very unelegant solution to the problem and you'd probably be better off with another suggestion. But you know, this is one way. I wish there were some kind of easy key remapping tool for linux.. Like, for example, sharpkeys for windows. Anyway, hope you find a good solution.

---

### Post by sceo on 2008-04-21
> **laga said:**
> Can you elaborate a bit on Pandora? Sounds interesting.

AFAIK, it's only available in the U.S. right now, technically -- but there are some proxy services available to listen to it in other countries.

Essentially, it's a streaming radio service that "seeds" stations based on a song or artist (or multiple songs or artists) that you enter.  Unlike Last.FM, which bases the new music you hear on what other people are listening to, Pandora uses the Music Genome Project, which dissects the songs musically (instrumentation, form, harmony, etc) to find new music you'd like.  I find it WAY more accurate than Last.FM.  When I listened to Last.FM, I always got Death Cab for Cutie songs, even though I hate DCFC... but since everyone else was listening to them, they kept coming up.  With Pandora, I am constantly finding new music.  You can thumbs-up / thumbs-down certain songs to further refine your taste.

---

### Post by greg963 on 2009-12-01
I have been able to fully integrate pandora into mythtv using prism and lirc. See the write up linked below or just look at the lirc section near the bottom.  As laga mentioned I primarily use irxevent, but also had to write a couple bash scripts to handle closing prism, and giving the flash player focus after launch.  You could also set up a script that would launch and then automatically do the focus hack after about 15 seconds. 

[http://ubuntuforums.org/showthread.php?t=1340349&highlight=Lirc](http://ubuntuforums.org/showthread.php?t=1340349&highlight=Lirc)

---

