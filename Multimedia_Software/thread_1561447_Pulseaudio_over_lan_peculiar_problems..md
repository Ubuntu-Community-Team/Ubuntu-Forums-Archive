---
title: "Pulseaudio over lan peculiar problems."
date: 2010-08-26
forum: Multimedia Software
---

### Post by kangarooks on 2010-08-26
Hi

I have pulseaudio on my desktop configured as a server.
On my lappy I have configured pulse to connect to desktop.

In that setup Totem Movie Player, and MAME do work, and when started on lappy sound gets through to the desktop.

Problem starts with vlc, mplayer and flashplugin in opera. Even though all of them get registered on desktop server as clients of pulseaudio, just like totem or mame, no sound gets through from mplayer, vlc or flash plugin.

Mplayer and vlc are configured to use pulseaudio, and they are listed on desktop as clients of pulse audio.

Any ideas what is going on?

---

### Post by kangarooks on 2010-08-28
Ok, now even totem player started to spew out errors in message box:

```
pa_stream_writable_size() failed: Connection terminated
```

Yet, mame still works ok, as in playing on lappy makes sound on desktop.

I'm totally puzzled ](*,)

---

### Post by kangarooks on 2010-11-27
All is cool and dandy with my new setup \\:D/

Please see my blog entry about the network headless pulseaudio central server connected to my stereo :)

[http://pleasanthacking.com/2010/11/28/linux-media-network/](http://pleasanthacking.com/2010/11/28/linux-media-network/)

:popcorn:

---

