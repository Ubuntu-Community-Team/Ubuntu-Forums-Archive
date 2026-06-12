---
title: "jackd, qjackctl only as root"
date: 2014-08-25
forum: Multimedia Software
---

### Post by drumanart on 2014-08-25
Hello.
Since an update a can run jackd, qjackctl & SCIDE only as root.

The failure I get:

drumanart@drumanart ~ $** jackd -d alsa**
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2014 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
self-connect-mode is "Don't restrict self connect requests"
audio_reservation_init
Failed to acquire device name : Audio0 error : Device reservation request with priority 2147483647 denied for "Audio0" via RequestRelease()
Audio device hw:0 cannot be acquired...
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server

drumanart@drumanart ~ $** groups**
drumanart adm cdrom sudo dip plugdev lpadmin sambashare audio

also I tried to (re-)add myself with:
**gpasswd -a drumanart audio**
without success

Thanks Martin

---

### Post by nova-deviator on 2014-09-21
hi,

not sure if that helps you, but I had the same issue, same error, and I solved it by removing an old ~/.asoundrc file... Check if you have one and perhaps just rename it to .asoundrc_bak or something. After that, my jack was happy to run.

Hope that helps.

best!

---

