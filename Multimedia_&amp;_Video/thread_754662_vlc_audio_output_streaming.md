---
title: "vlc audio output streaming"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by mjmcdonald21 on 2008-04-14
Ubuntu 7.10
VLC 0.8.6c

I have been able to stream audio through VLC over my local network without any trouble.  I would like to use VLC to capture the current audio output and stream that instead.  As much as I like VLC I prefer using Quod Libet as my music player.  

So far I haven't had much luck trying to capture the current output.  Any help would be appreciated.  Thanks in advance.

---

### Post by mjmcdonald21 on 2008-04-14
I am open to the idea of using a mic/line-in port but do not know how that would work either.

---

### Post by hugmenot on 2008-04-15
What I do since I upgraded to hardy is to stream audio through the network via Pulseaudio. This effectively obviated the need to run a cable across the room to my stereo because the stream goes over my wifi to an old laptop with a good audio output into the stereo.
PA is installed by default on hardy and the setup is fairly easy to make and robust. Any audio now can go through the PA tunnel, be played locally, or any combination.

---

