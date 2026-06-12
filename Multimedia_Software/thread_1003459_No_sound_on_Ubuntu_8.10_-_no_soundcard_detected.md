---
title: "No sound on Ubuntu 8.10 - no soundcard detected"
date: 2008-12-06
forum: Multimedia Software
---

### Post by ChrisBookwood on 2008-12-06
Hi,

I have no sound in 8.10.
lspci outputs *00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)*,
and aplay -l says *aplay: device_list:215: no soundcards found*...

I have [filed a bug on launchpad]("https://bugs.launchpad.net/ubuntu/+bug/302145"), but it's several weeks since anyone posted in there, so I thought I would give it a shot here.

I hope we can find a solution!

---

### Post by siddharthseth on 2008-12-06
Hi 
I couldnt find your chipset (ICH8) in ALSA list
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

Nevertheless if you want to give it a shot. Download the latest alsa source and try to compile and install the drivers.

cheers

---

### Post by ChrisBookwood on 2008-12-06
I'm not that familiar with the kind of magic of compiling _those_ types of things - I would like to be, but I'm not, I'm afraid.

I guess I have to wait till someone comes around with a solution.

---

### Post by ChrisBookwood on 2008-12-28
Here's the fix that did the job for me!

[https://bugs.launchpad.net/ubuntu/+bug/302145/comments/12](https://bugs.launchpad.net/ubuntu/+bug/302145/comments/12)

---

### Post by DuckDodgers on 2009-02-27
I know this is an old post, but it's very close to my problem.  When I tried the solution listed the first step went well but when I tried
sudo rmmod snd-hda-intel

my output was

ERROR: Module snd_hda_intel does not exist in /proc/modules

and when I tried
sudo modprobe snd-hda-intel

my output was

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-23-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Does anyone have any advice?

---

