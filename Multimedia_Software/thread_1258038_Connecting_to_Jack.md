---
title: "Connecting to Jack"
date: 2009-09-04
forum: Multimedia Software
---

### Post by Shugs81 on 2009-09-04
I've tried connecting to jack via qjackctl but it's having none of it...

I can run it from terminal as below

```
steve@steve-desktop:~$ jackd -d alsa hw:1
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

```

Then I can connect to Jack... but am I right in thinking this is setting up my onboard sound card HW:0 even though the command (I thought) was to set up using a usb device HW:1

any ideas? or can I just change the settings through jack? and do I have to amend the main sound settings too to use usb device for capture?

---

