---
title: "alsamixer settings not saved on restart or shutdown"
date: 2012-01-12
forum: Multimedia Software
---

### Post by CDSH on 2012-01-12
Howdy folks,

I've installed 10.04 on several computers now and never had a problem with alsamixer before.  I tried sudo alsactl store and it still does not save the settings.  I get no audio until I reset alsamixer.  Any ideas ?:confused:

---

### Post by CDSH on 2012-01-13
I seem to be at an impasse on this.  I've read several threads, but haven't found anything that resembles a solution as of yet.
 
Is there anyone out there that maybe could help me figure this one out ?
 
Thank you in advance !

---

### Post by CDSH on 2012-01-13
Through poking around in the SoundTroubleshooting docs, I found a possible issue.
 
 What currently is:
 
Driver version: 1.0.23 
Library version: 1.0.24.1 
Utilities version: 1.0.24.2
 
What the documentation says it should be :
 
 
Driver version: 1.0.24 
Library version: 1.0.24.1 
Utilities version: 1.0.24.2
 
The Alsa driver version is 1.0.23 and I need to change it to 1.0.24.  How does one do that ?  I haven't found that info in the documentation.

---

### Post by MoreOrLess on 2012-01-13
The first configuration you mention is the default for Ubuntu Natty/11.04 . There's nothing "wrong" with it and I doubt upgrading the kernel module will do the trick.

The official Ubuntu way to upgrade the kernel module is using the following ppa, but unfortunately, it is not up to date and doesn't work with the latest natty kernel: [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

---

