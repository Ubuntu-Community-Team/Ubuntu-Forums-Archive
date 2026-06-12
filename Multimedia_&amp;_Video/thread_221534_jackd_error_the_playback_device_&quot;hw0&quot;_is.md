---
title: "jackd error: the playback device &quot;hw:0&quot; is already in use."
date: 2006-07-23
forum: Multimedia &amp; Video
---

### Post by OneSeventeen on 2006-07-23
when I try to launch jackd, I just get told:```
15:01:57.310 JACK is starting...
15:01:57.312 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -D -Chw:0 -S
15:01:57.345 JACK was started with PID=8905 (0x22c9).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|64|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
15:01:57.639 JACK was stopped successfully.
15:01:59.414 Could not connect to JACK server as client. Please check the messages window for more info.
```
Any tips?
(I have Ubuntu and X-Chat running, that's about it.)

---

### Post by OneSeventeen on 2006-07-23
I rebooted and Jack starts up just fine.

---

### Post by christhemonkey on 2006-07-23
Some program was probably hogging your sound card.
The usual culprit is esd (the Enlightened Sound Daemon).
```
sudo killall esd 
```
Should do the trick in the future.

If its not esd, then its generally software that uses OSS (the open sound system) which is severly deprecated, but yet some programs insist on using them.

---

### Post by dolson on 2006-07-24
You can put the option to stop esd right in QjackCtl, so you don't have to remember to do it every time.

---

