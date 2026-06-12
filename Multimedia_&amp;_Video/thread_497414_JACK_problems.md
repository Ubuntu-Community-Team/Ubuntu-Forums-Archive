---
title: "JACK problems"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by smbm on 2007-07-10
Hi

I don't seem to be able to start JACK, here is the output:

```
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the capture device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
11:54:11.091 JACK was stopped successfully.
11:54:11.093 Post-shutdown script...
11:54:11.095 killall jackd
jackd: no process killed
11:54:11.317 Post-shutdown script terminated with exit status=256.
11:54:13.014 Could not connect to JACK server as client. Please check the messages window for more info.
```

Does anyone know of any way I can find out what is using hw:0? I've not got much else running. Could this be pulseaudio related?

Thanks for your time.

---

### Post by smbm on 2007-07-10
Ok, I've been fiddling around, Ardour can start JACK. I don't seem to able to start it from the JACK control panel though.

Any ideas?

---

### Post by pppZero on 2007-07-11
If ardour has already started its own jackd, then the soundcard will be in use, so you will not  be able to start it a second time ;)

To see what is curently using your sound card open a terminal and run:
```

lsof | grep /dev/snd
```

The name of the app using the sound card is in the very left column.

---

### Post by volksolwagen57 on 2007-09-09
how do you terminate these apps?

---

### Post by standards on 2007-09-20
"kill ####" where the number is to the right of the program name that grep command spits out. 

i'm having the same problem figuring out why hw:0 is in use when as far as i can tell, it's not. i'm using gutsy 64, so i also have a feeling the esd/pulseaudio transition is screwing with jack somehow. to the OP: did you ever figure this out? can anyone using gutsy run jack?

---

