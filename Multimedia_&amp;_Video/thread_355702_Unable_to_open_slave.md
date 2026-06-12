---
title: "Unable to open slave"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by Jadd on 2007-02-07
When I run lmms (after having closed esd), I get the following message:
```
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
```
which makes LMMS unusable. Any ideas? Thanks

---

### Post by Jadd on 2007-02-15
Please, anyone?

---

### Post by theonhighgod on 2007-03-13
When trying to be clever i set firefox dsp to "arts" as per [http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

and got the error

ALSA lib ../../../src/pcm/pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave

in the terminal when accessing a flash document, I know thats no help to you, but guess we have a similar kind of woe!

---

### Post by neaj on 2007-07-03
I'm getting this now, but when trying to launch mpd after suspend/resume .. 

 jean@klippie:~$ sudo mpd --verbose --no-daemon
Password:
binding to address for localhost
setFsCharset: fs charset is: UTF-8
reading DB
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

client-conf-x11.c: XOpenDisplay() failed
No audio_output specified and unable to detect a default audio output device

---

