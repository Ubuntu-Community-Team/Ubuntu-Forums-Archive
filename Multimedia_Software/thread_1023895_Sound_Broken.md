---
title: "Sound Broken"
date: 2008-12-28
forum: Multimedia Software
---

### Post by nightstraveler on 2008-12-28
So I'm pretty new at this, but I was trying to install Jack Audio Connection Kit and Ardour through Synaptic.  They installed without error but I couldn't get them to run correctly.  Now no sound works in ubuntu (8.10) even though I uninstalled Jack and Ardour.  Also the alsa in the panel has disappeared, presumably because it crashes.  I also install the GNOME Alsa mixer from synaptic, but it doesn't display any sliders and crashes if I go to sound card options.

---

### Post by markbuntu on 2008-12-28
It sounds like jack kludged your alsa. You can reinstall alsa to fix that and then you can get jack and ardour working properly. There is a lot to learn about sound in linux so you can start here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Just remember to follow the links to anything that interests you.

---

### Post by nightstraveler on 2008-12-28
Thanks Markbuntu, I'll try to make my way through that troubleshooting guide.  I've actually reinstalled the alsa package in synaptic when this happened, and that didn't help, but hopefully I'm missing something that is easy to do.

---

### Post by nightstraveler on 2008-12-29
So I tried reinstalling alsa following that guide, but that didn't help any.  I'm not getting the speaker icon next to the clock, so I feel like something isn't loading correctly, or has been corrupted.  Any idea what else I need to reinstall?

---

### Post by markbuntu on 2008-12-29
If you remove and reinstall alsa, you also need to reinstall your desktop and gdm as in the guide. There is also a section in there for restoring your default settings in the Sound Server Setup area, try that.

One trick you can try is to make a new user and login with that. If the sound works then you know the system is basically OK.

---

### Post by nightstraveler on 2008-12-29
Hey Mark,

So I had already reinstalled gdm and the desktop when I followed that guide you sent me the first time.  But I did try creating a new username with mixed results.  Still no sound, so that's bad.  But the alsamixer icon did show up in next to the clock.  I made sure nothing was muted and tried to make some sound and nothing.

Is there a clean way to reinstall ALL of the sound elements?
Other suggestions?

---

