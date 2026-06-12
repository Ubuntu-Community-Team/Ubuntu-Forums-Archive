---
title: "Open movie editor will not start"
date: 2009-02-17
forum: Multimedia Software
---

### Post by t.h.w. on 2009-02-17
Hello, 
I am a newbie tot Ubuntu and trying to get things to work. (Formus are great :popcorn:!)


I have a problem with Open Movie Editor.
It is installed as package of Ubuntu Studio ad I can find it i the start-tree. It started ok, but now it won't.

I have tried to re-install, de-install and install, via Syn.Package Manager, but the problem persists.

Now I have installed Cinelerra and with that the new version of Open Movie Editor. Still the same porblem: It will not start by using the 'shortcut' in th start-tree...

Anything else i can try?

Thanks!

---

### Post by gandaran on 2009-02-17
if it did work before then go to the hidden home user folder and delete all open movie folders you can find (reinstall won't fix the problem, deleting user configuration files can work), now you can restart open movie with the default settings, should work!

---

### Post by t.h.w. on 2009-02-17
@gandaran

Thanks for your suggestion. I have removed the .openme folder and the .openme.prefs but unfortinately this didn't help.

Any other suggestion?

Something else: The version of Open Movie Editor mentioned in the synaptic package manager is the older version, while the newer version was installed together with cinelerra...

Thanks!

---

### Post by gandaran on 2009-02-17
start open movie in terminal, copy and post the errors output here, it should say what is wrong.

---

### Post by t.h.w. on 2009-02-17
This is what I get in the terminal:

----8<-----------------------
Open Movie Editor Version: 0.0.20080523
Libquicktime Version: 1.0.2
Libquicktime API Version: 9
libavcodec Version: Lavc1d.51.38.0
libavformat Version: Lavf1d.51.10.0
/etc/debian_version:
lenny/sid
/etc/lsb-release:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"
----8<-----------------------
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
Jack Samplerate: 48000
terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
Aborted

I see a bad allocation and that Jack is giving problems? (Sounds like a bad gangster movie ;) )

---

### Post by gandaran on 2009-02-17
how much RAM do you have?
google "std::bad_alloc" you'll find many interesting articles about this

---

### Post by t.h.w. on 2009-02-18
Hello Gandaran,

I have 2 GB of RAM in my Acer Laptop with 200GB HD (app 150GB still free).

I understand that I run out of memory (?). But don't know what to do about that (ecxept putting in another 2GB and see what happens...) 

Only problems I have with Ubuntu is shutting down and then starting up. Sometimes I get the startup-logo double. Can this be because the RAM is not emptied? Can I flush the RAM?

Thanks!

---

### Post by gandaran on 2009-02-18
2 GB of RAM is enough, do you have a swap partition that equals your 2 GB Ram?
sorry can't help you with the rest.

---

### Post by t.h.w. on 2009-02-18
I'll have to check.
I don't know you large the swapfile is. I have installed Ubuntu from the LiveCD on one partition and let the installer of Ubuntu decide what to do... 

I have plans to make two (three) partitions, one for Ubuntu, one for Data and a third for Swap. Probably this will help.

Thanks for so far!

---

### Post by t.h.w. on 2009-02-18
I have 1.5 GB as swap.
In systemmonitor my memory is hardly used when I try to start OME...

Any suggestions?

---

