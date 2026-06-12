---
title: "no sound on dvd and tv playback"
date: 2008-09-03
forum: Mythbuntu
---

### Post by Nexusphreez on 2008-09-03
I am having an issue where I have sound when playing regular video files, avi, mov, mpg and such.  But when I try to actually watch a dvd or watch live tv, there is no sound at all.  I have tried checking the mixer and everything seems fine there.  Any ideas as to what would cause this?

---

### Post by tspan on 2008-09-05
If you use Totem with gstreamer backend (which is the default Movie Player in Hardy) try to remove it and install totem-xine package (Totem with xine backend) instead.

Gstreamer has many issues with dvd playback (see [http://live.gnome.org/DvdPlaybackWithTotem]("http://live.gnome.org/DvdPlaybackWithTotem") for details).

I had the same problem with dvd sound in Totem and installing totem-xine fixed it.

Hope this helps.

---

### Post by cyberkost on 2008-09-13
> **tspan said:**
> If you use Totem with gstreamer backend (which is the default Movie Player in Hardy) try to remove it and install totem-xine package (Totem with xine backend) instead.

Gstreamer has many issues with dvd playback (see [http://live.gnome.org/DvdPlaybackWithTotem]("http://live.gnome.org/DvdPlaybackWithTotem") for details).

I had the same problem with dvd sound in Totem and installing totem-xine fixed it.

Hope this helps.

I have the same issue as OP, but I'm already using totem-xine.  VLC exhibits the same problem with DVDs ... but at the same time all avi, mp3, audi-CD, etc. play fine.

---

