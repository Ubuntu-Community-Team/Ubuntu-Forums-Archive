---
title: "Gstreamer element dvdspu"
date: 2009-11-28
forum: Multimedia Software
---

### Post by Andrew Golightly on 2009-11-28
Hi all,

I am trying to play a DVD. Movie Player opens up and says it needs a plugin. Off it goes to search for **Gstreamer element dvdspu**, but tells me that **No packages with the requested plugin found**.

How do I get this plugin? VLC works.. but I have other apps that are asking for the same plugin.

thanks,
A

---

### Post by mc4man on 2009-11-28
It's probably the ugly plug-in, if you want to install the 5 most useful then just copy and paste this into a terminal. (all at once
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad \
gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly-multiverse \
gstreamer0.10-plugins-bad-multiverse
```

Sometimes karmic needs a restart, though shouldn't here

---

### Post by Andrew Golightly on 2009-11-28
Thanks mc4man. That fixed it! I only had 3 of those plugins installed.

---

### Post by AJenbo on 2009-12-20
Its the gstreamer0.10-plugins-bad, the way gstream plug ins are installed could realy be improved :(

---

### Post by Stevers on 2009-12-31
I think the gstreamer0.10-plugins-bad was the source of my problems, too.

I was watching a DVD I made. The first 10 minutes or so were going along fine and then the DVD started to spin down and then the movie completely stopped. It sounded like something in the drive broke. I panicked and ejected the disk as I didn't want the media stuck in my laptop. Further investigations showed that commercial DVDs no longer worked. Movie Player would open for a second or two and then close. VLC would report errors with (all? of) the files in the VIDEO_TS directory and some problem with setting the DVD title. Trying to copy files gave me input/output errors on the VIDEO_TS files. This is a dual-boot machine and the drive worked fine under Vista (failing under Ubuntu 9.10).

There were some other things that I did, including uninstalling VLC and changing permissions. I don't think that changed anything but I noticed that Media Player was missing dvdspu (from my recent VLC uninstall). So I found this forum and after installing gstreamer the DVD plays fine again, both Media Player and VLC. If it happens again, this will be the first thing I take off and put back on and hopefully that will be the ticket to get it working again. Maybe this'll help someone else, too.

-Stevers

---

### Post by Fitch on 2010-01-17
The plugins worked for me too.
Just one question, why are they called ugly and bad? I thought only my wife called me that?

---

