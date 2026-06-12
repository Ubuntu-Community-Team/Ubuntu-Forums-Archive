---
title: "record from dvb adapter during screen lock"
date: 2011-04-10
forum: Multimedia Software
---

### Post by MgFrobozz on 2011-04-10
I'd like to schedule extraction of the bitstream from my dvb adapter for a program that comes on about 1:30 in the morning local time. I have a script that schedules two other scripts using "at": one script uses mplayer to extract the stream; another script calls "killall mplayer" to kill the extraction after the program is done.

This works fine as long as I don't lock the screen or "switch from ..." my session, but fails if my session is locked and someone else logs in. I suspect it has something to do with hardware permissions while my session is locked. 

I'm running ubuntu 10.04, and I noticed when switching from release 9 to release 10 that if I was streaming audio to the speakers during my session, and I locked the screen, that the audio stopped. Did the permission policy on hardware devices change with release 10, and if so, is there a way to reserve/allocate a resource (eg, an audio output or a dvb input adapter)? Thanks ...

```

> cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"
> uname -srvmpio
Linux 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 unknown unknown GNU/Linux

```

---

