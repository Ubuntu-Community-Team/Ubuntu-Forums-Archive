---
title: "How to get Rhythmbox to play your iPod??"
date: 2010-10-10
forum: Multimedia Software
---

### Post by Alex090391 on 2010-10-10
I am running Ubuntu 10.04 LTS. I have been trying to get my iPod to play with Rhythmbox. The program reads my iPod and everything, but when i got to play a song it gives me an error saying, "Your GStreamer installation is missing a plug-in." What can be done to fix this error. I have been working hours on this and reading forums left and right, and still nothing has worked. I will post an image below to show what the error looks like.

thanks.

---

### Post by mc4man on 2010-10-11
This would take care of any related plugins, though possibly you already have

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

What format are the tracks? (if aac, then profile 1 or 2?

If you were to grab a track from rhythmbox w/ your cursor and drop onto your desktop can you play with another player?, vlc for instance

---

### Post by Sef on 2010-10-11
> This would take care of any related plugins, though possibly you already have

Code:
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly

Actually that may not work for a step was left out.

The easy way to get the plugins is this:

Applications > Ubuntu Software Center > Edit > Software Sources > tic universe and multiverse (they are in parentheses) > close

> (back in the software center now) > search: gstreamer > click on install for each one.

---

### Post by mc4man on 2010-10-11
> Actually that may not work for a step was left out.

Well I guess using the software center could/should be advised and it's always possible someone disabled the universe repo for some unknown reason. (or it's currently unavailable

---

