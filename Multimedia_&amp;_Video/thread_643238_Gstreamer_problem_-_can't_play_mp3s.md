---
title: "Gstreamer problem - can't play mp3s"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by flawsekno on 2007-12-17
I've been a happy Xubuntu user for about half a year. However, ever since I upgraded to Gutsy, I get the following error whenever I try to play an mp3 or m4a in Exaile:

> You do not have the appropriate Gstreamer plugin installed to play this file: file:///(filename)

I'm using Exaile 0.2.11, although this problem has persisted since 0.2.10 (the versions that I've had since upgrading to Gutsy). These are the packages that I have installed:

gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly-multiverse
w32codecs
xubuntu-restricted-extras

Is there something that I'm missing? While Totem, gxine, and Amarok work with mp3s (probably because they use xine instead of gstreamer), I much prefer Exaile to all of them. Ogg, flac, etc. files still work, but almost my entire music library is in mp3 because I have an iPod, so this is a pretty major inconvenience.

Alternatively, is there a way for Exaile to use xine instead of gstreamer? Thanks so much for the help!

---

