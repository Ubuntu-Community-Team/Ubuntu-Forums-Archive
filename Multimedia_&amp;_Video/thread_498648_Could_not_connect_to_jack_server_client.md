---
title: "Could not connect to jack server client"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by jazzman14 on 2007-07-11
I installed jack on regular ubuntu 7.04 not ubuntustudio, along with ardour. I set up jack according to a ubustu link somebody else posted. 

I get this: 

jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|64|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
17:34:02.600 JACK was stopped successfully.
17:34:02.601 Post-shutdown script...
17:34:02.601 killall jackd
jackd: no process killed
17:34:02.833 Post-shutdown script terminated with exit status=256.
17:34:04.556 Could not connect to JACK server as client. Please check the messages window for more info.



Any ideas?

---

### Post by jazzman14 on 2007-07-12
anyonee?

---

### Post by deadgobby on 2007-07-12
Try this and see if this will get jackd to go. You may need to install the Realtime kernel, but that kernel can be unstable. 

jackd -d alsa -d hw:0

GObby

---

### Post by jazzman14 on 2007-07-12
After running the jackd -d alsa -d hw:0...i get the same message

---

### Post by fredj on 2007-07-12
It is likely that your soundcard will not accept 64 frames try 128. You won't get as low a latency
but that is how things are for some soundcards.

---

### Post by jazzman14 on 2007-07-13
I changed from 64 to 128, and now i just get a message that it can't connect because sh:artsshell: not found..that seems to be whats stopping it now.Thanks!

---

### Post by jazzman14 on 2007-07-13
aanyonee?

---

### Post by jazzman14 on 2007-07-14
After running qjackctl in terminal...Iget this:

XError: Bad Device: invalid or uninitialized input device 167
Major Opcode: 144
Minor Opcode: 3
Resource Id: 0x0
Failed to open device

XError: Bad Device: invalid or uninitialized input device 167
Major Opcode: 144
Minor Opcode: 3
Resource Id: 0x0
Failed to open device

Warning No Locale Found: /usr/share/locale/qjackctl_en_us_UTF-8.qm

---

