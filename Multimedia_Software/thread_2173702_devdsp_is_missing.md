---
title: "/dev/dsp is missing"
date: 2013-09-10
forum: Multimedia Software
---

### Post by lither on 2013-09-10
I'm using Ubuntu 12.04. When I use the Python library call ossaudiodev.open("w"), I get the error mesage "No such file or directory: '/dev/dsp'", and indeed /dev/dsp does not exist. This used to work under Ubuntu 10.04. I've searched for advice on this subject, and found nothing useful, despite some being marked "answered". I've installed the packages oss4-base, oss4-dev, liboss4-salsa2 and liboss4-salsa-dev, to no avail. Any ideas?

---

### Post by tgalati4 on 2013-09-10
I happen to be running a 9.04 machine.  Do you have alsa-oss installed?


tgalati4@tpad-Gloria7 /dev $ apt-cache policy alsa-oss
alsa-oss:
  Installed: 1.0.17-1
  Candidate: 1.0.17-1
  Version table:
 *** 1.0.17-1 0
        500 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Packages
        100 /var/lib/dpkg/status

OSS is an old linux audio framework (open sound system, I believe) that was replaced by ALSA.  A wrapper is used to maintain compatibility with older software that makes OSS audio calls.  I believe /dev/dsp is installed by alsa.  So make sure you have the complete ALSA framework installed.

---

### Post by lither on 2013-09-11
Yes, I have it installed:
rick@Zebedee:~$ sudo apt-cache policy alsa-oss
alsa-oss:
  Installed: 1.0.25-1
  Candidate: 1.0.25-1
  Version table:
 *** 1.0.25-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages
        100 /var/lib/dpkg/status
So, no, It doesn't install /dev/dsp. I did belatedly find that there's a python interface to alsa available, but it's still in development and not part of the official Python library yet. I find it hard to believe that there's currently no official way to play audio from Python. I must be missing something.

---

### Post by Yellow Pasque on 2013-09-11
Well, installing OSS4 should give you /dev/dsp, but Ubuntu ripped out OSS support a long time ago, so I doubt that's what you really want. You should purge the OSS4  packages and hope you didn't bork all your audio.

>  I believe /dev/dsp is installed by alsa.
It's not. For programs that still use OSS-style /dev/dsp, you can emulate it with padsp:
```
padsp <program>
```

---

### Post by Yellow Pasque on 2013-09-11
Oh, and I thought pyalsa was the official ALSA lib?
[https://launchpad.net/ubuntu/+source/python-pyalsa](https://launchpad.net/ubuntu/+source/python-pyalsa)

---

### Post by lither on 2013-09-11
> **Temüjin said:**
> Well, installing OSS4 should give you /dev/dsp, but Ubuntu ripped out OSS support a long time ago, so I doubt that's what you really want. You should purge the OSS4  packages and hope you didn't bork all your audio.

Quite right. The oss4 packages did bork the audio, but mercifully removing them returned things to normal.

> 
It's not. For programs that still use OSS-style /dev/dsp, you can emulate it with padsp:
```
padsp <program>
```

Ah. Thank you. That works, and is at least a good temporary fix.

---

### Post by lither on 2013-09-11
> Oh, and I thought pyalsa was the official ALSA lib?
[https://launchpad.net/ubuntu/+source/python-pyalsa](https://launchpad.net/ubuntu/+source/python-pyalsa)
I'd previously found pyalsa through [http://pyalsaaudio.sourceforge.net/pyalsaaudio.html](http://pyalsaaudio.sourceforge.net/pyalsaaudio.html), which is where I got the impression that it's not official. I'll look into it. Thanks again.

---

