---
title: "JACK Sound and Open Movie Editor Question?"
date: 2009-05-30
forum: Multimedia Software
---

### Post by celem on 2009-05-30
My Ubuntu Jaunty AMD-64 9.03 sound is working fine but when I try to use Open Movie Editor (Version 0.0.20080102-2.1ubuntu1) all I get is static. Although I have read that Open Movie Editor can work without jackd (Version 0.116.1-3ubuntu3) installed, I am beginning to doubt it. I installed jackd, ran the daemon and then Open Movie Editor provides silence instead of static, but still no sound. I can't find a lot on configuring jackd so I am sure that I've done something wrong. Better yet, if Open Movie Editor "can" work without jackd, can anyone explain how? Thanks in advance.

OUTPUT OF JACKD:
```
ecomer@ubu-squirrel:~$ jackd -d alsa
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
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback

```

OUTPUT OF OPEN MOVIE EDITOR
```
ecomer@ubu-squirrel:~$ openmovieeditor
When submitting a BUG report, or SUPPORT request, please include the following information:
----8<-----------------------
Libquicktime Version: 1.1.0
Libquicktime API Version: 9
libavcodec Version: Lavc52.11.0
libavformat Version: Lavf52.24.1
/etc/debian_version:
5.0
/etc/lsb-release:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
----8<-----------------------
Enhanced3DNow! detected
SSE2 detected
Jack Samplerate: 48000
[mp3 @ 0x270f2f0]mdb:91, lastbuf:0 skipping granule 0
When submitting a BUG report, or SUPPORT request, please include the following information:
----8<-----------------------
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6200 LE/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 180.44
GL_MAX_TEXTURE_SIZE = 4096
----8<-----------------------

```

See also, my post in the Open Movie Editor board:
[http://tinyurl.com/nxbkhd](http://tinyurl.com/nxbkhd)

---

### Post by nalle on 2009-06-24
I have the same problem, any fixes? Should this be reported as a bug in jaunty rather then here?

---

### Post by Unknown 4242 on 2009-06-29
> **nalle said:**
> Should this be reported as a bug in jaunty rather then here?

Nope I've got it to and I'm running Hardy.  Must all FOSS video editors have such issues?

---

### Post by benjaminad on 2009-12-21
Anyone figure this out yet. I have the same problem on UE 2.2 64bit. Works fine on 32bit though. HELP! This is a great little editor. What a waste if no one can fix this. I am to ignorant to fix it.

---

### Post by celem on 2009-12-21
I am on different hardware now with 9.04 amd64 and it works without problem. Linux just didn't properly recognize the hardware that I was using, which I have now dedicated to Windows XP and it now sits in the corner, powered off.

---

