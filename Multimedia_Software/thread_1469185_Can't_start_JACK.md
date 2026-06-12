---
title: "Can't start JACK"
date: 2010-05-02
forum: Multimedia Software
---

### Post by HyperFlexed on 2010-05-02
Using Karmic 9.10, AMD64 (x86_64)

Hi, I've poured over all the threads here and elsewhere, followed every FAQ I can, and I can't seem to get JACK running with ALSA.

I tried starting JACK with qtjack, and I get the following:

```
00:11:53.337 JACK was started with PID=25592.
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|-|1024|40|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
new client: alsa_pcm, id = 1 type 1 @ 0xf8c140 fd = -1
00:11:53.388 Could not connect to JACK server as client. - Overall operation failed. Please check the messages window for more info.
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 40 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: got smaller periods 8 than 40 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
00:11:53.441 JACK was stopped successfully.
00:11:53.441 Post-shutdown script...
00:11:53.442 killall jackd
jackd: no process found
00:11:53.856 Post-shutdown script terminated with exit status=256.
```

Aside from the fact that linux audio is beyond my comprehension, this tells me very little.

So I figured, maybe there's a conflict. Linux seems challenged when it comes to sharing the soundcard

```
johnny@johnny-desktop:~$ fuser -v /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  johnny    24779 F.... pulseaudio
/dev/snd/seq:        johnny    25289 F.... qjackctl.bin

```

I've tried "pulseaudio --kill", but it seems to bring itself back to life, which would make sense as I hear Ubuntu uses it for system sound.

I can manage to get Renoise running with ALSA alone, but I need JACK to connect with other applications. The way I understand it ALSA is the workhorse, and JACK sits on top of it allowing programs to connect together. If anyone can point me to some comprehensive documentation on how these systems work together I'd be grateful.

JACK will start for about a second, then it crashes.

Let me know if you need any more information.

---

### Post by HyperFlexed on 2010-05-02
Okay, I can get jack playing nicely if I first execute

```
jackd -dalsa
```

I noticed the error log said "cannot load driver module alsa"

Any way to make qtjack load it before starting Jack?

I've considered writing a shell script that calls "jackd -dalsa" and then starts qtjack, but that seems kind of odd. Isn't jackd the jack server itself? I'm confused.

I would read the man page, but my jackd man page is missing for some reason. Anyone know how I can fix that?

---

