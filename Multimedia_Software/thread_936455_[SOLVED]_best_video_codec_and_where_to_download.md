---
title: "[SOLVED] best video codec and where to download?"
date: 2008-10-02
forum: Multimedia Software
---

### Post by timstone on 2008-10-02
I was trying to watch a video online earlier and when it was streaming it was really blocky and looked like crap, figured it was just the codec that I installed.  

Just wondering if there is a set of codecs that will let me watch all types of videos and if maybe one codec is better than another?

---

### Post by knattlhuber on 2008-10-02
This is an excellent Multimedia HOWTO:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
Just follow the instructions and you are all set.

---

### Post by gandaran on 2008-10-03
it depends on what player you running
for totem or any gstreamer based player, install the gstreamer-plugins (codecs) find them in synaptic, alternatively you can buy the gstreamer-fluendo codecs.
for mplayer or mplayer clone/based player, you need the w32codecs or w64codecs for 64-bits system, just add the medibuntu repository to synaptic to get them.
for any XINE based player, just make sure libxine-ffmpeg is installed and the w32codecs too.
for VLC you don't need to install any codecs, it already comes installed with codecs.

---

