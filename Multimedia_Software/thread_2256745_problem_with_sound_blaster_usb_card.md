---
title: "problem with sound blaster usb card"
date: 2014-12-14
forum: Multimedia Software
---

### Post by carl.alv on 2014-12-14
Hi everyone,

I have ubuntu 14.04 installed on a small acer aspire laptop. I bought recently a sound blaster x-fi hd card along with a 2.1 set of speakers. The first time i pluged it two drivers appeared (sound blaster HD analog and sound blaster HD digital), I selected any of those and it worked just fine. Then I installed the qas mixer and rebooted (with the card plugged i think). Upon restart the sound blaster HD digital controler was no longer found so i used the analog one, but now the system is just stereo (not 2.1) and the subwoofer is taken as the right speaker.

Any ideas o what to do would be appreciated!

---

### Post by carl.alv on 2014-12-14
Well, this solves my problem temporarily [http://ubuntuforums.org/showthread.php?t=1098579&highlight=sound+blaster+x+fi](http://ubuntuforums.org/showthread.php?t=1098579&highlight=sound+blaster+x+fi)
but I have to shut down pulseaudio and restart alsa manually everytime I reboot. Does someone knows how to do this automatically (with a script for example)?

tnx

---

### Post by Rob Sayer on 2014-12-16
Well, at least you aren't wanting to purge pulseaudio like many with issues.

There's a pretty good description of how to disable pulse (along with why you souldn't purge it) here:

[http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

---

