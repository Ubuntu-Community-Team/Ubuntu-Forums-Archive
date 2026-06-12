---
title: "cannot play encrypted DVDs"
date: 2010-05-07
forum: Multimedia Software
---

### Post by uncertain on 2010-05-07
Hi, everyone, first post, so please be gentle! ;)

I'm running UNR 10.04 (fresh install) on a new Acer Aspire1 250 and just cannot get encrypted DVDs to play at all (as far as I can tell), using any media-player software.  I'm having the most luck so far with xine (it is at least properly playing a DVD that I think must not be encrypted), so I'd like to start with trying to get xine working. 

Details:
Running xine-ui 0.99.5+cvs20070914-2.1
I have installed ubuntu-restricted-extras, libdvdnav4, libdvdread4, libdvdcss2, gstreamer-plugins-bad, gstreamer-plugins-ugly.
I'm using a LaCie external DVD to (try to) play these.

Problem:
After inserting the DVD, I start up xine, which will play usually a brief introduction to the DVD (like the FBI warning, studio logo, maybe start up the menu) and then crash, giving the error message:
```
The source can't be read.
Maybe you don't have enough rights for this, or source 
doesn't contain data (e.g.: not disc in drive).
(/media/GOODWILL/VIDEO_TS/VTS_06_1.VOB)
```The last line of course varies with the DVD, and there are many of these messages (one per track, I think).  

Like I suspect, does this mean that xine doesn't realize that libdvdcss2 is there (or some codec)?  If so, how do I tell it where to look?  I'm glad to provide other technical information if you can tell me what would help!  Thanks much, help is greatly appreciated!

---

### Post by WinterRain on 2010-05-07
Have you tried VLC player?

---

### Post by madphatboy2 on 2010-05-07
I've found Medibuntu to be extremely helpful to get all sorts of formats to play.

---

### Post by uncertain on 2010-05-07
> **WinterRain said:**
> Have you tried VLC player?

Thanks for the tip, just tried it, but no luck.  It starts to load the disc, flashes a black display window, and then just goes back to waiting for me to tell it what to do.

> **madphatboy2 said:**
> I've found Medibuntu to be extremely helpful to get all sorts of formats to play.

I've got the Medibuntu repository set up.  Is there a specific package or set of packages you think would help?

---

