---
title: "Running jackd as user"
date: 2009-03-09
forum: Multimedia Software
---

### Post by lhoffmeyer on 2009-03-09
Want to be able to run jackd as user.
Currently /usr/bin/jackd is set root:root.

What do I change/modify so that user can run jackd?

Want to run jackd from command line as user and not
sudo jackd.

Lance

---

### Post by lhoffmeyer on 2009-03-09
The error I get is:


$jackd --timeout 4500 -R -d alsa -d hw:2 -r 44100 -z shaped -p 128 
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1209289040, from thread -1209289040] (1: Operation not permitted)
cannot create engine

---

