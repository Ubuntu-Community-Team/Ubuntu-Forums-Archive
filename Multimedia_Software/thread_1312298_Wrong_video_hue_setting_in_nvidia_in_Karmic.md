---
title: "Wrong video hue setting in nvidia in Karmic"
date: 2009-11-03
forum: Multimedia Software
---

### Post by MiKom on 2009-11-03
Hi,
after upgrading to Karmic colors in all video playback programs (Totem, vlc) seem to be wrong. According to this:
[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

there are some bugs in drivers, but the solution proposed in this answer doesn't work for me.

My graphic card is GeForce 8400M GS (Mobile) and I use binary nvidia driver (185 series, from main repository).

Thanks

---

### Post by VertexPusher on 2009-11-03
It's not a driver bug but a wrong hue setting in Totem ("Movie Player"). Once you correct that, all the other media players will work fine, too.

---

### Post by harrykar on 2009-11-27
> **VertexPusher said:**
> It's not a driver bug but a wrong hue setting in Totem ("Movie Player"). Once you correct that, all the other media players will work fine, too.

Tnx a lot SOLVED :arrow:

---

### Post by tpeelen on 2009-11-29
Thanks. I've done all sorts of things including reinstalling gstreamer plugins, changing gstreamer-properties and more ...

Ofcourse I should have checked at the forum right away. Great!

---

### Post by tjwilli on 2010-07-03
I'm having this problem also. I went in gconf-editor and saw that the hue was set to zero, but playing back ogv files still changes the hue.

---

### Post by tjwilli on 2010-07-03
Looks like I needed to go to Edit->Preferences, Display tab, Reset to Defaults button.
That seemed to do the trick.

---

