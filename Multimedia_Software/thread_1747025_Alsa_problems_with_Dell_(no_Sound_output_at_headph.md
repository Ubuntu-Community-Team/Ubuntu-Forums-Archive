---
title: "Alsa problems with Dell (no Sound output at headphone jack)"
date: 2011-05-02
forum: Multimedia Software
---

### Post by jpthank on 2011-05-02
before some updates everything works fine, after some updates( including nvidia driver)...then no more
earphone sound. 


Alsa problems with Dell (no Sound output at headphone jack) 
machine: Dell Precision M4500

only have the problem with headphone.(well, plug in my earphone
no sound at all, unplug, the sound works fine)


cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD81B1C5


checked the article:
[http://doc.ubuntu-fr.org/audio_intel_hda#acer](http://doc.ubuntu-fr.org/audio_intel_hda#acer)
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/126936](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/126936)

dont know what should i actually add to the alsa-base.conf.

only ADD the following line to /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=dell-s14

reboot, doesn't work still. 
set to analog headphones or analog output 
doesn't work.


please help me.

---

### Post by jpthank on 2011-05-03
I check lordraiden's "Comprehensive Sound Problem Solutions Guide"
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

now, the problem is solved.


sudo modprobe snd-hda-codec-idt.

:popcorn:

---

### Post by lidex on 2011-05-04
So it's not loading the alsa module for your codec? Do you have to run that modprobe command after every boot?

---

