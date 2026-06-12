---
title: "Multimedia Preview Not Working in Nautilus on Gutsy"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by spamking2000 on 2007-10-23
Hey - After upgrading from Feisty to Gutsy I've had a few errors. Most of them I've been able to fix/clear on my own, but this one I haven't been.

In Feisty I was able to preview sound files in Nautilus... a normal feature. For some reason, that functionality is gone. I checked my settings, anything >5MB should come up with a preview if I hover the mouse over it.

mpg-123, mpg123-esd, and vorbis-tools are installed.

As an example, MP3's play fine in Totem/VLC/MPlayer/XMMS, just not when previewed in Nautilus or on the desktop.

Any ideas?

---

### Post by spamking2000 on 2007-10-24
A little more to add. Not sure if its related, but for sound events, I swear used to allow me to choose either WAV or OGG format, now I'm limited to WAV w/o OGG support.

Also, I tried testing ESD in the Sound Preferences. Everything else (ALSA, OSS, etc) gave me a nice tone when playing the test. ESD on the other hand gave me this:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server

Oh, what to do, what to do?

D

---

### Post by naboj on 2007-10-24
I've had the same problem! 
But found the solution by installing:
apt-get install mpg123
apt-get install mpg123-esd
apt-get install pulseaudio-esound-compat

You can read more in this thread [http://ubuntuforums.org/showthread.php?p=3604804]("http://ubuntuforums.org/showthread.php?p=3604804")

---

### Post by spamking2000 on 2007-10-26
@Naboj - THANK YOU, THANK YOU, THANK YOU!!!!!

That worked! I installed pulseaudio-esound-compat via apt-get and its all working now!

Don't know how the upgrade affected it though... pulseaudio itself was installed, and when I installed pulseaudio-esound-compat, it did remove the base pulseaudio package.

Thanks so much, and I'll bet this will help other folks out there as well!!

Thanks,
spamking2000

---

