---
title: "Quicktime on Firefox"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by Ratsock on 2007-06-25
Hi all,
Having some trouble getting quicktime videos to work in firefox. I've tried it with the mplayer and totem plugins for mozilla and it doesn't work. :(

My firefox setup is a 32bit one on my 64bit AMD (because of the flash plugin issue).

Any help appreciated :)

---

### Post by ubu-for on 2007-06-25
Try [this](http://ubuntuforums.org/showpost.php?p=2546697&postcount=2).

---

### Post by Ratsock on 2007-06-25
I tried that page but the problem is that when i click the video link i get asked to save the video, not play it. And if i go to a page with embedded video i cant get a rightclick menu. I just see the "click to download this plugin" placeholder

---

### Post by ubu-for on 2007-06-26
> **Ratsock said:**
> I tried that page but the problem is that when i click the video link i get asked to save the video, not play it. And if i go to a page with embedded video i cant get a rightclick menu. I just see the "click to download this plugin" placeholder

You really have uninstalled the "totem-mozilla" plugin and installed the "mozilla-mplayer" plugin?

Maybe you need the following additional codecs for Totem or the [w32codec](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.1_i386.deb) for MPlayer.

libxvidcore4
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
gstreamer0.10-gl
gstreamer0.10-pitfdll
libquicktime0

---

