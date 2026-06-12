---
title: "microphone stopped working"
date: 2010-11-03
forum: Multimedia Software
---

### Post by thenzero on 2010-11-03
I'm having some pulseaudio weirdness.  Up until this evening, my built-in microphone worked fine with skype, google voice, etc.  Tonight while talking on google voice, I made the mistake of trying to adjust the microphone volume at the same time.  Suddenly the volume cut down to a tiny, tinny little sound.  Now I can't get the microphone to work normally again.  Some weird facts:

1) the built-in microphone still works fine in audacity and gnome-sound-recorder
2) the built-in microphone still works in Windows
3) the built-in microphone shows sound input in the pulseaudio applet->Volume Meter (Recording) but NOT in the pulseaudio mixer!
4) if i plug a microphone into the mic in jack, that audio now works in skype, google voice, and shows up in the pulseaudio mixer
5) if i scream into the built-in microphone, it registers the barest little sound

Hardware:

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

on an Asus T101MT

running Ubuntu 10.04, kernel 2.6.32-24, all audio packages up to date

From googling around, I understand other people have had problems with this sound card.  However, it was working right up until I adjusted the volume while the mic was in use tonight!

Things I've tried to fix the problem:

1) Rebooting 400 times
2) Reinstalling pulse audio
3) Deleting all pulse audio config files I could find (i.e. .pulse folder in my home directory)
4) Setting every mixer bar in every mixer program to max and unmuted
5) Logging into XFCE and Gnome, as both myself and a new user

I'm at a loss here.  I've got this system otherwise configured exactly how I want it and I would hate to have to reinstall over something like this :(

Edit:  Apparently this is a known bug- [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447259](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447259)

---

### Post by thenzero on 2010-11-03
If it's of use:

[http://www.alsa-project.org/db/?f=d9ee58127d59fa97f2a058a12fb8a8cfdd987bf8](http://www.alsa-project.org/db/?f=d9ee58127d59fa97f2a058a12fb8a8cfdd987bf8)

---

### Post by thenzero on 2010-11-04
The problem was fixed by muting the left channel but not the right channel in the pulseaudio volume mixer, as referenced in this thread: [http://ubuntuforums.org/showthread.php?t=1306561&page=6](http://ubuntuforums.org/showthread.php?t=1306561&page=6)

Hope this helps others with the same problem.

---

