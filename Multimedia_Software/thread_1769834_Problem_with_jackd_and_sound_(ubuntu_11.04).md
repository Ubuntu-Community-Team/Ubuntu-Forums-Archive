---
title: "Problem with jackd and sound (ubuntu 11.04)"
date: 2011-05-28
forum: Multimedia Software
---

### Post by jorritTyb on 2011-05-28
Although sound in general works (there are sounds from my desktop) I cannot seem to start jackd.

I'm running qjackctl and then I try to start jackd. This is the output I get in the messages window:

> 
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
Cannot lock down memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel PCH at 0xfbff4000 irq 43
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
19:23:14.109 JACK connection change.
19:23:14.110 Server configuration saved to "/home/jorrit/.jackdrc".
19:23:14.111 Statistics reset.
19:23:14.124 Client activated.
19:23:14.152 JACK connection graph change.
Cannot lock down memory area (Cannot allocate memory)


The status says 'Started' but I'm a bit suspicious. When I then start a program like espeak it also complains about:

> 
Cannot lock down memory area (Cannot allocate memory)


What can I do to fix this?

Thanks

---

### Post by jorritTyb on 2011-05-28
Hmm, if I start qjackctl from root I don't get the last memory error but still espeak isn't working. It now says:


> 
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started


Any clue?

---

### Post by jorritTyb on 2011-05-29
Nobody has a solution?

---

