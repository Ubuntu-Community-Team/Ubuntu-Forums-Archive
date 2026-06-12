---
title: "Playing .flv files in Totem."
date: 2009-05-20
forum: Multimedia Software
---

### Post by michael91 on 2009-05-20
I've recently installed Linux Mint, and am unable to watch .flv files in Totem. When I try to, Totem comes up with "The playback of this movie requires a Flash demuxer plugin which is not installed." I've tried looking through the Synaptic Package Manager, but can't find it. What's the name of the plugin? Is it even in the Synaptics?

---

### Post by gandaran on 2009-05-20
ensure you have all gstreamer0.10 plugins installed, totem plays flash videos just fine.
doesn't linux mint have all codecs installed by default?

---

### Post by albinootje on 2009-05-20
> **michael91 said:**
> Totem comes up with "The playback of this movie requires a Flash demuxer plugin which is not installed."

Did totem not give you the option to install that extra plugin ?

In Ubuntu you can do :
```

sudo apt-get install ubuntu-restricted-extras

```
will install all or almost all of the packages needed for video playback. Don't know whether that is applicable in Linux Mint.

---

### Post by meka4996 on 2009-05-23
try this one
[http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)

---

