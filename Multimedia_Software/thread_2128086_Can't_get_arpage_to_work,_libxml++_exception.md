---
title: "Can't get arpage to work, libxml++ exception"
date: 2013-03-22
forum: Multimedia Software
---

### Post by enoc22 on 2013-03-22
Hi All,
   New to the forum here but glad to be a part of it.
I've recently installed ubntu studio 12(64bit) with the hopes of expaning my music horizons.
I've had my eye on arpage(midi arpginator) for the last year or two but was never able to get it to work on my old install of fedora.
I was able to compile and install it. But when i went to run it from the comand line i get the following:
```
on_error(): Premature end of data in tag arpeggiator line 1

libxml++ exception: Document not well-formed
on_error(): Premature end of data in tag arpeggiator line 1

libxml++ exception: Document not well-formed
on_error(): Premature end of data in tag arpeggiator line 1

libxml++ exception: Document not well-formed
on_error(): Premature end of data in tag arpeggiator line 1

libxml++ exception: Document not well-formed
jackd 0.122.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

```
the
```
libxml++ exception: Document not well-formed
on_error(): Premature end of data in tag arpeggiator line 1
```
bothered me but the window came up and i went and started qjackctl and conected arpage to yoshimi.
When i played a key on the virtual keyboard the note would play but no arpegination, just the straight note.

Any thoughts of what i might be doing wrong? i know it can work, i've seen videos of it on youtube, i'm just at my whits end of what to do next to get it working.

Any help would be appreciated.

Thanks
Oliver

---

### Post by BlinkinCat on 2013-03-22
Hi Oliver,

For the future you may like to have a look at the Ubuntu Studio links within NewDocs (found in my signature)

Cheers - :p

---

### Post by enoc22 on 2013-03-22
Thanks BlikinCat...I didn't know ubuntu studio had it's own forum section, Is there a way i can get this post moved over to that?


Oliver

---

