---
title: "How Do I NOT Use fglrx?"
date: 2006-03-21
forum: Multimedia &amp; Video
---

### Post by wsmoser2004 on 2006-03-21
I have a laptop with an ATI Mobility Radeon 9200 card and a widescreen LCD.  When I first installed Kubuntu, I was using the default "ati" driver, and everything worked pretty well.  A month or so later, I needed to give a presentation with the laptop, and apparently the "ati" driver does not do well when hooked up to a projector (the colors were very strange and the image was cut off).  I decided to give fglrx a try (with the drivers included with Breezy, 8.16.20 I think), and it sort of worked...except that it forced my resolution to 1024 x 768 (non-widescreen), and my normal resolution is 1280 x 800 (widescreen).  This worked great on the projector, but looked lousy on the laptop's LCD.  

After the presentation, I tried to play around with getting the new fglrx drivers (8.22.5)...I'd heard that they supported widescreens.  To my surprise, after I had them installed and I rebooted, X no longer came up...I just got a black screen, and I couldn't Ctrl-Alt-F1, Ctrl-Alt-Backspace, or anything.  I read around a little bit, and it looks like the newest fglrx drivers don't work with my card for whatever reason.  So I decided to go back to the "ati" drivers, since they were pretty good anyway (I don't play many games, so graphics acceleration isn't an issue for me).  However, now that I've switched back, my frame rate for screensavers and glxgears is terrible!  I'm guessing fglrx must have changed something, and "ati" doesn't like it?  What is this, and how can I change it back?

Or, if anyone else has this same card and knows how to get fglrx working, that would be great too.

---

### Post by wsmoser2004 on 2006-03-21
Well, I managed to get fglrx working with the newest driver, 8.23.7.  However, I had the same problem with this new driver....I had to follow the instructions on [this]("http://www.x1000forums.com/index.php?showtopic=5073") site to actually get it working.  I guess the driver was not recognizing my LCD display or something.  Now I have 1500 fps in glxgears, so I'm happy. :p

---

