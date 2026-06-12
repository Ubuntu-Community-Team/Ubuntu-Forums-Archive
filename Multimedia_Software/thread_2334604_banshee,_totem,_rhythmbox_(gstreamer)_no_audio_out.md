---
title: "banshee, totem, rhythmbox (gstreamer) no audio output"
date: 2016-08-21
forum: Multimedia Software
---

### Post by G_Muh on 2016-08-21
Hi folks, [this is a confirmed bug]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/1178272") which prevents proper sound output in Gstreamer apps in Lubuntu. It's present in Lubuntu Xenial 16.04 but a related bug report goes as far back as Lubuntu Raring (13.04). It's pretty nasty in that big-name apps such as Banshee and Rhythmbox will fail to work out of the box in Lubuntu.

The problem is that Ubuntu installs [FONT=courier new]gstreamer1.0-pulseaudio[/FONT] per default, but Lubuntu does not use pulseaudio. Instead, Lubuntu should install [FONT=courier new]gstreamer1.0-alsa[/FONT] per default.

Can somebody who knows how to handle dependency bugs take this on or refer it up the food chain? Thanks! [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/1178272](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/1178272)

**Workaround**

If you cannot get audio output in a Gstreamer application such as Banshee, Totem, or Rhythmbox in Lubuntu, try the following command:

[FONT=courier new]sudo apt install gstreamer1.0-alsa[/FONT]

If you're having problems playing back certain codecs such as MP3, additionally try

[FONT=courier new]sudo apt install gstreamer1.0-plugins-ugly[/FONT]

---

### Post by mc4man on 2016-08-21
nv

---

### Post by Bucky Ball on 2016-08-21
> **G_Muh said:**
> Can somebody who knows how to handle dependency bugs take this on or refer it up the food chain?

If you're looking for a developer this is the wrong place. We are all volunteers here and not affiliated with Canonical. Launchpad is the right place to deal with bugs, particularly if this is a known one and people are dealing with it already. If that is the case, consider it already 'up the food chain'. You might like to add your fix there if it's not there already. You may also like to try approaching developers directly. Not sure of the correct link for that.

---

### Post by G_Muh on 2016-08-21
I suspect that developers sometimes read forums, surf in from search engines, etc.

Thus, I leave this thread here for them to find.

I've also brought it up on IRC.

---

### Post by mc4man on 2016-08-21
That bug report seems a bit convoluted. ( & old
It implies that sound would work with pulseaudio, - when you install Rb or banshee aren't pulseaudio libs installed as a recommend? (- the rec. is gstreamer1.0-pulseaudio which pulls in other pulse packages), in Ubuntu recommends are treated as depends.

In any event the bug (new one) should just simply request gstreamer1.0-alsa be added to lubuntu-meta. As it stands 6 other gstreamer packages are already included so one more shouldn't be such a big deal.

---

