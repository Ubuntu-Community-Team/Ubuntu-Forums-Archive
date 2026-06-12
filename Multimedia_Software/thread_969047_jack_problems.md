---
title: "jack problems"
date: 2008-11-03
forum: Multimedia Software
---

### Post by Mzwo on 2008-11-03
hi,

two problems arose: first, qtjackctl literally lost its face - the main windows remains blank, although by guessing where, for instance, the start and stop buttons are, i can still start and stop jack. annoying, but to date not a real hurdle. i tried reinstalling it, problem not solved. 

the second problem arose recently (after reinstall) and yields this in the qtjackctl message window:

11:42:56.624 Patchbay deactivated.
11:42:56.757 Statistics reset.
11:42:56.953 ALSA connection graph change.
11:42:57.185 ALSA connection change.
11:43:00.440 Startup script...
11:43:00.441 artsshell -q terminate
11:43:01.584 Startup script terminated with exit status=256.
11:43:01.584 JACK is starting...
11:43:01.585 /usr/bin/jackd -R -m -dalsa -r44100 -p1024 -n2 -D -Chw:2 -Phw:2
11:43:01.614 JACK was started with PID=6502.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:2|hw:2|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:2
control open "hw:2" (No such file or directory)
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
11:43:01.805 JACK was stopped successfully.
11:43:01.805 Post-shutdown script...
11:43:01.805 killall jackd
jackd: no process killed
11:43:02.214 Post-shutdown script terminated with exit status=256.
11:43:03.824 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

why? any hints? (hw:2 was not connected this time, doesn't make a blind bit of difference whether it is).

funny things is: occasionally, after the umpteenth reconnect, it would work. 

running 8.04 studio. 

much obliged,

Mzwo

---

### Post by Mzwo on 2008-11-05
bump

---

### Post by Mzwo on 2008-11-07
bump

---

### Post by Mzwo on 2008-11-08
bump

li'l' help?

Mzwo

---

### Post by Mzwo on 2008-11-08
forget it. upgrade to 8.10 solved the problem. whyever.

Ta,
Mzwo

---

