---
title: "Poor quality sound"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by moitio on 2007-02-18
Hello.

I'm using Edgy, and I've been having problems with my sound. I noticed that the sound output from my onboard soundcard is very very poor under Linux. I've tried listening to music through Windows with the official drivers (Realtek) and I don't notice any degradation of sound (through a 3.5mm jack to phono cable plugged into an amplifier). On normal PC speakers I also notice the sound degradation under linux. I'd like to find out if this is a common problem or not, and if there's a way of getting better sound quality.

Many thanks in advance, 
Tom Moitie

---

### Post by r4ik on 2007-02-18
You could try a player with an equalizer.
Amarok has one XMMS has a better one i.m.o but you have to like the interface.

Good luck !

---

### Post by moitio on 2007-02-18
No, I've tried Amarok, XMMS, MPD, Rhythmbox, VLC. All of them output an almost muffled sound when played at quite high volumes. I'm sure its something to do with gstreamer or a sound server. The files I'm playing are MP3s.

---

### Post by r4ik on 2007-02-18
I suppose you read every guide available.
do you have these installed ?

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

From,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

---

### Post by moitio on 2007-02-18
I've been reading as many guides as I can handle. I have all of them installed, yes. I read on the official wiki that libxine-extracodecs interferes with gstreamer0.10-plugins-ugly, or the other way round and its either/or. I did try removing both (one at a time) and I had no luck.

---

### Post by Junk_head on 2007-02-18
Have you tried the alternative MPD (Music Player Daemon) and a front-end client?

---

### Post by r4ik on 2007-02-18
I feel much more expertize than i can come up with :)
Good luck !

---

### Post by moitio on 2007-02-18
> **Junk_head said:**
> Have you tried the alternative MPD (Music Player Daemon) and a front-end client?

Yes, I have, it's what I use when I'm not using Rhythmbox, and I use phpMp as the front-end. It still gives the same result.

---

