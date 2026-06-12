---
title: "Installing JACK 0.102.20 from source"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by tuedel on 2007-01-10
Hi,
I recently decided to upgrade my JACK to version 0.102.20.
configure (with *--prefix=/usr*), make and make install worked fine so far, at least I couldn't spot any errors.
When I try to launch jackd via qjackctl after installing it, I get the following error:
```
18:29:14.328 Startup script...
18:29:14.329 artsshell -q terminate
18:29:14.608 Startup script terminated with exit status=256.
18:29:14.608 JACK is starting...
18:29:14.608 jackd -R -dalsa -r48000 -p1024 -n2 -D -Chw:0 -Phw:0 -m -S -H -M
18:29:14.614 JACK was started with PID=30050 (0x7562).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|hwmon|hwmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
[COLOR="Red"]18:29:16.753 Could not connect to JACK server as client. Please check the messages window for more info.[/COLOR]
```
When I *make uninstall* the new JACK version and reinstall the 'jackd' package from the Ubuntu repository via apt-get, everything works fine again, so it shouldn't be a config issue with JACK.

Any suggestions?

(Sorry if this issue has been addressed before, I didn't find any solutions on the forum search and Google)
(Oh, and simply keeping the old version of JACK is **not** a solution for me ;) )

---

### Post by tuedel on 2007-01-14
No ideas? :(

---

### Post by ssavelan on 2007-01-15
The exact same thing happened to me... 

There is something wrong with how ubuntu deals with jack...

I had the exact same problem... I am thinking that I will try to let the ubuntu dependencies catch up to the jack and just wait for the dusty stable versions to finally come down the pipe with apt-get.

If anyone is successful using the latest build of JACK with ubuntu..... I would love to hear.....

---

### Post by tuedel on 2007-01-17
At least I'm not alone with my problem ;)

Does anybody know if they're including JACK 0.102.20 in Feisty Fawn?

---

### Post by tuedel on 2007-02-01
Bump.

Did no one succeed in building jackd from source on ubuntu yet?

---

