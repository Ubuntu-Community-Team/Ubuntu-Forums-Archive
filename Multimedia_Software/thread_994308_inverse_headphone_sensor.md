---
title: "inverse headphone sensor"
date: 2008-11-26
forum: Multimedia Software
---

### Post by helmuthauser on 2008-11-26
Hello,

I am quite desperate. When I first installed Kubuntu on my laptop everything (including sound) worked out of the box. 

Suddenly I have the problem that my loudspeakers ONLY bring sound if my headphone is plugged IN. But there is no sound in my headphones then. 

In my understanding, the standard situation would be that the laptop should detect a plugged headphone and then change the sound output from the loudspeakers to the headphone (as it worked before).

please help,
helmut

More info can be found under (made with utils_alsa-info.sh)
[http://www.alsa-project.org/db/?f=a3b4e067dfd27614bf2f33e327842098116711ca](http://www.alsa-project.org/db/?f=a3b4e067dfd27614bf2f33e327842098116711ca)

smaller version:
Using Kubuntu 8.04

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf1200000 irq 22

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko

---

### Post by helmuthauser on 2009-06-03
It turns out that it was a hardware failure.

problem solved :-)
helmut

---

