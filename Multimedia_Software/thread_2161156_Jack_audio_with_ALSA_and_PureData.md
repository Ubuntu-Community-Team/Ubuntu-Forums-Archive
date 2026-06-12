---
title: "Jack audio with ALSA and PureData"
date: 2013-07-09
forum: Multimedia Software
---

### Post by malachipclover on 2013-07-09
I just received a laptop from a friend to fix up.  I cleared the hard drive and put Ubuntu on it.  This was just yesterday, so it's a fresh install.  I'm trying to run PureData, but I'm having issues with it.  When I try to start it, it says

```
JACK: unable to connect to JACK server
JACK: server returned status 17
```

I downloaded qjackctl, and upon pressing the start button I get this

```
[COLOR=#999999]13:08:50.488 JACK is starting...[/COLOR][COLOR=#990099]13:08:50.490 /usr/bin/jackd -dalsa -r44100 -p1024 -n3 -D -Chw:0 -Phw:0[/COLOR]
jackd 0.122.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
[COLOR=#999999]13:08:50.507 JACK was started with PID=3800.[/COLOR]
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
[COLOR=#999999]13:08:50.911 JACK was stopped successfully.[/COLOR]
[COLOR=#FF0000]13:08:52.687 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
```

Is there a package missing that I can install or is it something more in depth, and what would I have to do?  Any help is appreciated, thanks.
I'm running vanilla Ubuntu 13.04.

---

