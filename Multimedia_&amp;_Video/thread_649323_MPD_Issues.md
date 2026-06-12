---
title: "MPD Issues"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by a12ctic on 2007-12-24
I've been having some issues with MPD.

First when I start it it says.

```
arctic@andrew-desktop:~$ sudo /etc/init.d/mpd start
Starting Music Player Daemon: ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

E: client-conf-x11.c: XOpenDisplay() failed
mpd.

```

then if i try to use it or i just run mpd it says

```

unable to bind port 6600: Address already in use

```

however in my mpd.conf I have it bound to localhost. Any ideas?

also, when i type sudo dpkg-reconfigure mpd no dialog comes up.

---

### Post by monroetransfer on 2008-01-19
I am having the exact same problem! The strange thing is, I'm now in a relatively clean install of Gusty. Everything's updated, and it won't run, but on my previous OS configuration, which was a complete mess (I manually had turned dapper kubuntu into feisty ubuntu), everything worked fine!

sure would be nice to get some help with this...

---

### Post by bartkl on 2008-05-29
I had the same problem, but once I closed all other applications involved with my sound card (Quod Libet, even Firefox when Flash is loaded) it worked fine. 

I have some other weird similar problems. If I run any music player, very often (maybe always) Firefox doesn't use sound (youtube videos are silent).
Then when I close my players, it works.

Would it be a bug?

---

### Post by crypticreign on 2008-06-10
I'm fairly certain that this is a bug! Perhaps with Pulse Audio?  I had the same exact issue with mpd.  Also noticing that I couldn't get sound in in vlc or rhythm box in Ubuntu while running Virtual Box.

Any update?  Any fix?

---

