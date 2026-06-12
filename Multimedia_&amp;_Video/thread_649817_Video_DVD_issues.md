---
title: "Video DVD issues"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by abelthorne on 2007-12-25
Hello,
I have a desktop PC which runs Ubuntu 7.10 (upgraded from previous versions). On it, I have set up DVD playback using EasyUbuntu and it works quite well.

I also own a Dell XPS M1330 laptop and I have problems playing video DVD on it. It has a fresh install of Gutsy and I can't use EasyUbuntu on it (seems broken since Gutsy), so I've had to manually install the packages needed for DVD  playback.
I installed w32codecs, a bunch of gstreamer plugins, libdvdcss2, libdvdread3, libdvdnav4 and ubuntu-restricted-extras.
I've tried three DVD with Totem, VLC and MPlayer and have a lot of issues, such as crashes with MPlayer, no playback with Totem (pauses itself), garbage sound & picture with VLC and so on. One of the DVD seems to play fine with Totem but behaves oddly.

I've had to use regionset to set my DVD drive to region 2 (I live in France) as it had none set. Also, strangely, gxine seems to play the DVD but stops after a few seconds complaining that it can't decrypt CSS (although libdvdcss2 is installed from Medibuntu).

Are there known hardware issues that could explain this behaviour ? Or maybe I miss some packages ?

---

