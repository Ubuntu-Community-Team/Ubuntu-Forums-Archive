---
title: "Playing WMA files"
date: 2010-05-22
forum: Multimedia Software
---

### Post by Zian on 2010-05-22
I've set up the multiverse, installed the restricted extras, and installed w32codecs but I can't get WMA files to play.

Movie Player just says that:
The playback of this movie requires a Windows Media Audio 9 decoder plugin which is not installed.

---

### Post by mc4man on 2010-05-22
If you're on hardy then you could try installing the pitfdll gstreamer plugin, it may work, it may not.

Your best bet would be mplayer or a xine based player with libxine1-ffmpeg installed. (they will both play wma3(pro) and wmal (lossless

If your are running karmic wma3(pro can be enabled for gstreamer (enabled by default in lucid

---

### Post by Zian on 2010-06-09
Oops, I forgot to update my distro info.

I'm actually using Ubuntu 10.04 LTS.

---

### Post by mc4man on 2010-06-09
> I'm actually using Ubuntu 10.04 LTS.

If you have the basic gstreamer plugins - (am assuming you do), then the only wma that can't be decoded with a gstreamer app are wmal (lossless) and mss2 (microsoft screen codec)
```

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

If your files are wmal then you'll need a 32 bit mplayer or a decent xine engine player and w32codecs installed (plus libxine1-ffmpeg for xine.

Vlc can decode wmal but only if a 32 bit version and when built with --enable-dmo option. (even then support is somewhat borked

---

