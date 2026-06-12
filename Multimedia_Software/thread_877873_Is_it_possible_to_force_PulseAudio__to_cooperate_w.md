---
title: "Is it possible to force PulseAudio  to cooperate with Music Player Daemon?"
date: 2008-08-02
forum: Multimedia Software
---

### Post by ffatman on 2008-08-02
I've installed MPD and Sonata client under Ubuntu 8.04. Everytime i've tried install/start/restart MPD the system's answer is:

```
Konfigurowanie mpd (0.13.1-3ubuntu1) ...
 * Starting Music Player Daemon mpd                                             
 * creating /var/lib/mpd/tag_cache... 
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
*** PULSEAUDIO: Unable to connect: Connection refused
```

Is there anybody who had resolved that problem?

---

### Post by MrHippocampus on 2008-08-04
There is some information about how to solve this problem on the pulseaudio page on the mpd wiki, [link]("http://mpd.wikia.com/wiki/PulseAudio").

---

