---
title: "Oscilloscope, jackd, jack-dssi, hw:0 in use, and other woes."
date: 2009-06-12
forum: Multimedia Software
---

### Post by Asday on 2009-06-12
After apt-get installing several packages, this is my current predicament.

I try to open Oscilloscope.  Nothing.

I try to open Oscilloscope from the console.

```
jack-dssi-host: Warning: DSSI path not set
jack-dssi-host: Defaulting to "/usr/local/lib/dssi:/usr/lib/dssi:/home/asday/.dssi"


jack-dssi-host: Error: Failed to connect to JACK server

```

For some reason (I think google told me to), I got to trying "jackd -d alsa -d hw:0" to see what happens.

```
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
```

Again, google had bewildering suggestions.  "sudo killall esd"

```
esd: no process killed
```

So, nothing killed, surprise surprise "jackd -d alsa blah blah blah" does the same thing.

Now.  Question time.  WITH YOUR HOST, ASDAY, WHO, AS A CHANGE OF ROLES, HAS ALL THE QUESTIONS.

First and foremost, how hard, and at which point, do I need to kick Oscilloscope in the head?  Is there a particularly quick way to make it work?

Why is it not connecting to the jack server?

What's using hw:0?  ...  What *is* hw:0?

Thanks in advance.

---

### Post by Asday on 2009-06-13
Well, superduper bump-with-new-info time.

If I do:

```
sudo qjackctl
```

Then (in a new terminal)

```
sudo jack-dssi-host ll-scope.so
```

It launches.  Still not sure how to use it, and I don't like having to run it as a superuser, so the original questions stand.

---

