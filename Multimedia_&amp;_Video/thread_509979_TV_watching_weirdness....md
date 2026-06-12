---
title: "TV watching weirdness..."
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by MsChevyKat on 2007-07-26
I've been using one flavor of linux or another for many years, and setting up this new computer, came up with a problem I've never had before!

When watching tv, using any tv program, if I watch in the small window that comes up, all is good.

If I go to resize the window, to make it larger, the computer completly shuts down!  Other than this, the computer does not do anything strange at all.

The computer is running an athlon 64 x2 4200+

The motherboard is a GeForce6 100SM-M.  It has integrated video, the GForce 6100.

This is really weird. Anyone know what this could be?  This only happens with the TV, no other video apps, or anything else.

Thanks. :)

Oh yeah, I'm running Feisty, the 32 bit version.

---

### Post by MsChevyKat on 2007-07-26
bump! :D

---

### Post by MrHippocampus on 2007-07-26
hmmm, thats very strange. Are you using the official (restricted) nvidia driver?

---

### Post by MsChevyKat on 2007-07-26
> **MrHippocampus said:**
> hmmm, thats very strange. Are you using the official (restricted) nvidia driver?

Yes sir, I am.

I've done many stress tests on the video, like player with beryl for hours, running screensaver, youtube, java.

I haven't tried watching movies yet, new install and haven't installed codecs.

It only does that with television.  I've been up 12 hours, no problems otherwise.

I also tried using the generic vesa driver with the same result.

---

### Post by MsChevyKat on 2007-07-26
I'm using the nvidia-glx driver.

Should I try the nvidia-glx-new?

---

### Post by MrHippocampus on 2007-07-26
Strange, I would find out what the name of the card your using is and then post a bug report on launchpad [here]("https://launchpad.net/ubuntu"), the people there may have a better idea of whats going on.

---

### Post by MsChevyKat on 2007-07-26
Well, I'm guessing now that it was a corrupted install.  I did a clean re-install, and everything seems normal now.

---

### Post by MsChevyKat on 2007-07-27
I guess I spoke too soon. Went to resize the tv window...and BLAM!  System shutdown. :(

---

### Post by MrHippocampus on 2007-07-27
What TV card are you using?

---

### Post by MsChevyKat on 2007-07-28
> **MrHippocampus said:**
> What TV card are you using?

It's a  Leadtek TV2000XP pci card.  It uses the bttv driver.

I moved this card from my old dell to this new machine, it worked fine over there.

Works fine here, as long as I don't try to resize the window.  If I use the controls to make it fullscreen it works fine, or if I keep the small default window, but I go to resize, the computer shuts off!!

Very strange indeed.

---

### Post by MrHippocampus on 2007-07-30
Well, all I can suggest is looking on google to see if anybody else has the same problem, if not you could try filing a bug for ubuntu on  [launchpad]("https://launchpad.net/ubuntu"), since it restarts your machine I think its worthy of their attention.

---

