---
title: "Can't set real-time priority"
date: 2010-12-20
forum: Multimedia Software
---

### Post by Graemej on 2010-12-20
Running lubuntu 10.10 kernel 2.6.35-24-generic

Am using jackd2 and can't set real-time priority.
ulimit -r -l reports:
real-time priority 0
max locked memory  64

What I have tried:
sudo dpkg-reconfigure -p high jackd2
Which built the /etc/security/limits.d/audio.conf
I am in the group audio

Running qjackctl as root allows me to run the audio in realtime so it seems to be a permissions problem and it seems to me that lubuntu does not read the /etc/security/limits.d/audio.conf file when I boot.

I have tried adding:
@audio   -  rtprio     99
@audio   -  memlock    unlimited
to /etc/security/limits.conf even though that is now deprecated.

I sure could use some help here thanks.

---

### Post by ShadowTek on 2010-12-20
Staring a program with **nice** allows you to set its thread priority to maximum.

---

### Post by Graemej on 2010-12-20
Tried adding to audio.conf
@audio   -  nice      -19

still no good. I think that rtprio being set to 99 would make nice unnecessary but am grateful for anything which could send me on the right trail.

---

### Post by Graemej on 2010-12-22
To reply to my own post, it looks more and more that it is an LXDE problem rather than an ubuntu one. With ubuntu and xubuntu the same setup works fine.

I would still like some help with the problem though - thanks.

---

