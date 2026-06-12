---
title: "Banshee"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by fazavon on 2007-09-17
OK  I have Banshee 12, I am having an issue with it playing songs. Every other song tells me that there has been a unknown error and skips it. 

This is new, it did not do this until about three days ago. I have tried completely removing banshee, reimporting the muzik, did not help.

Is anyone else having this issue and or does anyone know how to fix this issue?


Thanks

//j

---

### Post by Thyme on 2007-09-17
Have you installed any updates recently? What's the output if you run it from the terminal by entering "banshee"?

---

### Post by fazavon on 2007-09-17
not any updates that pertane to banshee

this is the out put

ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
Debug: [9/17/2007 6:29:03 PM] (Loading audio profiles) - /usr/share/banshee/audio-profiles
Debug: [9/17/2007 6:29:03 PM] (Default player engine) - GStreamer 0.10
Debug: [9/17/2007 6:29:03 PM] (Audio CD Core Initialized) - 
Debug: [9/17/2007 6:29:03 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_5680806180804987
Debug: [9/17/2007 6:29:04 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_5680806180804987
Debug: [9/17/2007 6:29:04 PM] (Audioscrobbler starting protocol engine) - 
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
Performing compatibility update on playlist 'New Playlist 1'
Performing compatibility update on playlist 'New Playlist 2'
Performing compatibility update on playlist 'New Playlist 3'
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71

---

### Post by Thyme on 2007-09-17
Not sure I can offer any valuable help, unfortunately.

What I would do, however, is install the latest banshee and additionally configure it with either OSS for sound and check whether that also gives the same problem as ALSA. Although, honestly,    I would probably first try the latest Banshee version :)

Cheers

---

### Post by clonek on 2007-09-17
Seems like ALSA is broken for some reason. Thats about all the help I can offer really . 

Maybe try rebooting if you don't reboot often.

---

### Post by fazavon on 2007-09-18
No I fixed it.

ALSA lib pcm.c:2145snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib pcm.c:2145snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71

was where I had tried to enable 7.1 surround sound, and after seeing that i guess i failed at that. But I undid the changes made for that, and now all is well again.

Thanks to all who posted.

//j

---

