---
title: "ubuntu 10.10 have system sound and 'Audacious'  sound but no sound from Rhythmbox"
date: 2010-10-20
forum: Multimedia Software
---

### Post by mdc001 on 2010-10-20
Hope there is some help around for this vexing problem.

Upgraded from 10.04 to 10.10.  All sound programs working prior to upgrade.

I have sound from the 'system' (for example at startup) and from "Audacious" music player.

I can't get any sound from Rhythmbox, Banshee or Movie Player.

Rhythmbox reports, after trying to play a file, "Configured audiosink bin1 is not working."

Worked through some of the Ubuntu's "Sound Troubleshooting" page but I do have sound (some).

Any ideas would be greatly appreciated.
Regards,
Marc

---

### Post by CosineQuaNon on 2010-10-21
I posted some tips on fixing this at the Arch Linux Wiki, take a look (it's the last section on the page): [http://wiki.archlinux.org/index.php/Exaile#.22Playback_error_encountered.21_Configured_audiosink_bin0_is_not_working.22](http://wiki.archlinux.org/index.php/Exaile#.22Playback_error_encountered.21_Configured_audiosink_bin0_is_not_working.22)

---

### Post by mdc001 on 2010-10-21
Thanks for the suggestion.  npviewer.bin process was not running.  I was able to play a .wav file using movie player and rhythmbox but not an mp3 nor ogg file.  In fact, rhythmbox crashes after failing to play a number of songs.  I see by other posts that others are having challenges with the sound system.  Most of those seem to be of the "no sound whatsoever" category

---

### Post by neo_1in on 2010-11-08
I am having the same problem when using Lubuntu 10.10. Sound is working fine in vlc and gnome-mplayer but exaile gives this error:
```
Playback error encountered!
Configured audiosink bin1 is not working.
```
I went through the wiki page and sound card configuration seems to be okay. Any solutions?

---

### Post by chirojoseph on 2010-11-16
bump and superbump..

same boat as neo here...lubuntu freshly installed on a new asus netbook with 2gb ram..
it worked amazing out the box with Easy Peasy  (i think it was that one) and i liked it quite a bit so immediatly installed with lubuntu but SAME ERROR....cant find much info about ol autosink 1

anybody? totally clueless and without SOUND on my jukebox

---

### Post by confused_user on 2010-11-22
same here....was fine in 10.04

---

### Post by weekend warrior on 2010-11-25
Check and make sure you have the GStreamer plugin for ALSA installed, current version is gstreamer0.10-alsa

---

### Post by Spiritfall on 2010-11-30
> **weekend warrior said:**
> Check and make sure you have the GStreamer plugin for ALSA installed, current version is gstreamer0.10-alsa

I have the GStreamer plugin for ALSA installed and I still have this issue. Is there any other way I can fix this?

---

### Post by weekend warrior on 2010-12-04
The alsa plugin was what made the difference on my system, but also check that these are installed.

gstreamer0.10-ffmpeg 
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-ugly

---

### Post by weekend warrior on 2010-12-04
A couple of others to try as well

gstreamer0.10-esd
gstreamer0.10-puseaudio

found on this page
[http://www.inductiveload.com/solutions-to-errors/](http://www.inductiveload.com/solutions-to-errors/)

> 
Error: Playback error encountered! Configured audiosink bin1 is not working (or bin0)
Problem: Exaile cannot find an audio sink to connect to with GStreamer. You need to install one that matches your audio sink, such as ALSA or PulseAudio.
Solution: Install the relevant package and restart Exaile. For Ubuntu, this is gstreamer0.10-alsa, gstreamer0.10-esd, gstreamer0.10-puseaudio or similar. According to this, on Arch Linux this may also be caused by a Flash object fighting for ALSA.

HTH

---

### Post by Spiritfall on 2010-12-04
I had all of them installed except gstreamer0.10-esd. I installed it but my problem persists. I read something about the problem being my 5.1 setup but I don't remember where I've read. At least I hope the problem will be fixed in Natty. I'm currently using Grooveshark for music and smplayer and vlc for movies.
Thank you for your help.

---

### Post by Yellow Pasque on 2010-12-04
> **Spiritfall said:**
> I have the GStreamer plugin for ALSA installed and I still have this issue. Is there any other way I can fix this?

If you're running pulseaudio, manually set the sinks to pulseaudio:
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink pulsesink
```

Also try updating to the latest stable gstreamer with a PPA: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by zeating on 2010-12-09
Bump same problem

---

### Post by dominus_sapiens on 2010-12-16
> If you're running pulseaudio, manually set the sinks to pulseaudio

After endless problems with Banshee, Totem and Rhythmbox that were clearly down to Gstreamer, having found no solution at all in my many hours of trying, I can happily say that this miraculously worked. Very impressed!

---

### Post by stevenswall on 2011-06-06
THIS FINALLY WORKED - Please Mark as [SOLVED]

gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink pulsesink

---

