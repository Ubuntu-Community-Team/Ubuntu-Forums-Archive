---
title: "Matroska/H.264 playback problems"
date: 2009-04-13
forum: Multimedia Software
---

### Post by Aintaer on 2009-04-13
I am trying to play h.264 encoded videos inside mkv containers with Totem.  However, upon opening, Totem shows Playing, and stops at 0:00. I get no sound and no video.

I've tried looking for solutions to this problem, have already installed the gstreamer bad and ugly plugins.  Unlike other posts I've found here, my problem is not choppy playback but complete inability to play.

This problem happened before with MP3 files, but after installing the codec, it worked.  So I suspect it's something along those lines again.

---

### Post by d_in_Conduct on 2009-04-14
VLC will play .mkv files.  Other that that,  I usually have to extract the video from the .mkv container.  Since most of my audio and video work is done with windows software,  I usually use that platform when converting files.  I haven't done much with it in Linux.

---

### Post by lovinglinux on 2009-04-14
Follow [this tutorial](http://ubuntuforums.org/showthread.php?t=766683) and you will be able to play everything. I use gnome-mplayer and smplayer. Smplayer provides more options and better subtitle support, but gnome-mplayer has a nice and simple interface.

---

### Post by Aintaer on 2009-04-14
I tried the how-to, but wasn't able to get ia32-libs package.  I don't know if that is necessary...

I will try some other media players.  What I'm really looking for is something that has Gnome integration (so I can use my media hotkeys).  What are my choices these days?

---

### Post by wolfen69 on 2009-04-14
> **Aintaer said:**
> wasn't able to get ia32-libs package.

install the medibuntu repos.
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

---

