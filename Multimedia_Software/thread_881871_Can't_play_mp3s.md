---
title: "Can't play mp3s"
date: 2008-08-06
forum: Multimedia Software
---

### Post by thusimos on 2008-08-06
Hardy

I've got sound.  I can hear the system sounds, and streaming audio through the web.  

When I try to play an mp3 in MPlayer, or Rhythmbox, or Audacious, it just stops.  No sounds, no warnings, no error messages or terminal output.  

In Rhythmbox, for example, if I select a file and hit play, it reads the id3 info, puts the song length next to the scrollbar, and doesn't play.  The play button stays depressed.  

How do I troubleshoot this with no error messages?

---

### Post by perlluver on 2008-08-06
> **thusimos said:**
> Hardy

I've got sound.  I can hear the system sounds, and streaming audio through the web.  

When I try to play an mp3 in MPlayer, or Rhythmbox, or Audacious, it just stops.  No sounds, no warnings, no error messages or terminal output.  

In Rhythmbox, for example, if I select a file and hit play, it reads the id3 info, puts the song length next to the scrollbar, and doesn't play.  The play button stays depressed.  

How do I troubleshoot this with no error messages?

Do you have the MP3 codecs installed?

---

### Post by thusimos on 2008-08-06
I think so.  The Synaptic Package Manager shows the ubuntu-restricted-extras is installed.  Version 15.2

---

### Post by sayakb on 2008-08-06
See the Ubuntu Customization tutorials link in my sig below for instructions on how to add medibuntu and install W32codecs.

---

### Post by JoshuaRL on 2008-08-06
Alright, make sure you have the lame engine.

```

sudo apt-get install lame

```
See if that helps.

---

### Post by cprofitt on 2008-08-06
> **thusimos said:**
> Hardy

I've got sound.  I can hear the system sounds, and streaming audio through the web.  

When I try to play an mp3 in MPlayer, or Rhythmbox, or Audacious, it just stops.  No sounds, no warnings, no error messages or terminal output.  

In Rhythmbox, for example, if I select a file and hit play, it reads the id3 info, puts the song length next to the scrollbar, and doesn't play.  The play button stays depressed.  

How do I troubleshoot this with no error messages?


If you restart and try using Rythmbox first can you then play sounds?

There is a bug right now in the 32bit version that causes problems with sound... basically if you use flash first then client apps do not have any sound... if you use client apps first then flash gets no sound.

[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/254389](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/254389)

---

### Post by limasierra on 2008-08-06
You can also try vlc player```
sudo apt-get install vlc
```

---

### Post by thusimos on 2008-08-06
It works now.  I rebooted and tried Rhythmbox before opening anything else.  Must be that bug.

---

