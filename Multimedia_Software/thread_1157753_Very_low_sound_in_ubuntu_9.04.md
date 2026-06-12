---
title: "Very low sound in ubuntu 9.04"
date: 2009-05-13
forum: Multimedia Software
---

### Post by gautam888 on 2009-05-13
Just few days back i installed ubuntu jaunty n also i updated it but still the sound is very low...
also i tried alsamixer, gnome-alsamixer.. all the levels are at 100% but still very low sound.
I am using compaq desktop SR1620IL and my sound card is HDA Intel ALC880
Please help, thanks

---

### Post by upptown on 2009-05-13
Check your OSS settings.  Don't know why this impacts me as I've configured my sytem for PULSE.  Anyways, every time I reboot my OSS mixer volume defaults to 70%.

---

### Post by gautam888 on 2009-05-13
thanks buddy for ur reply.. but still the problem is same, no improvement. :(

---

### Post by xc3RnbFO8P on 2009-05-13
Try in Terminal:
> alsamixer

---

### Post by gautam888 on 2009-05-13
i tried it.. and also gnome-alsamixer in terminal.. still very low sound

---

### Post by albinootje on 2009-05-13
> **gautam888 said:**
> Just few days back i installed ubuntu jaunty n also i updated it but still the sound is very low...


I've seen the low volume problems on a few laptops, you might want to try the newest Alsa software.
This howto shows you how :
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
See also :
[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

---

### Post by djbushido on 2009-05-13
What sound are you using to test? Like what program? If you can tell us this (as well as what sound platform you have - OSS, ALSA, Pulse, or Jack) that would help us a lot. Also, try and switch what sound platform you are using (like stated above) to see if that gets you anywhere, or switch hardware devices.

---

### Post by gautam888 on 2009-05-13
after appending the line

options snd-hda-intel model=asus-dig

in /etc/modprobe.d/alsa-base.conf

---

### Post by superbiskit on 2009-05-13
Ubuntu 9.04 (network dist-upgrade)
nVidia NForce2 pulse-audio mixer
Gnome desktop

Very similar symptoms.  When I log-in, the audio is muted.  If I un-mute I get audible sound, but even at 100% it isn't very loud.

---

### Post by mgarrana on 2009-08-10
i 've ran alsamixer from the terminal and increased PCM and front levels , and this has worked for me
i am using ubuntu 9.04 on dell latitude D830

---

