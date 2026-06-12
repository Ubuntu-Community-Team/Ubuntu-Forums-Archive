---
title: "quicktime and flv playback problem"
date: 2009-04-27
forum: Multimedia Software
---

### Post by ROUBOS on 2009-04-27
Hi people,
well I'm using Ubuntu 8.10.
Recently re-formated due to videocard issues with 9.04 :(

Anyway, the thing is that I cannot play the Apple Trailers in Mozilla properly. I mean the totem plugin plays them, but it does not resize them properly to fit right inside the player in firefox.

The other question I have is, VLC does not play .flv files, and mplayer with zine does not resize them to fit properly in the window.

How do I set both these things up? The .mov files in mozilla so I can watch the trailers properly, and to be able to play .flv files. (flv not in the browser, but files I have in my local folders..)

Thanks...

---

### Post by ROUBOS on 2009-04-28
no one?

---

### Post by ROUBOS on 2009-04-28
If anyone else needs to know, I used this link

[http://ubuntuforums.org/showthread.php?t=766683&highlight=mozilla+video+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=mozilla+video+playback)

In part-2:

Gecko Media Player is similar to mplayerplug-in, as it uses GNOME MPlayer to play virtually all formats, but works well without the need of adding any configuration options. Installation and setup is simple, just copy and paste the following commands into the terminal:

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

sudo apt-get install gnome-mplayer gecko-mediaplayer

OK and don't forget you need to enter preferences and select X11 video output. Plays SWEET !!!!!!!!!

---

### Post by meka4996 on 2009-05-23
try this one...
[http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)

---

