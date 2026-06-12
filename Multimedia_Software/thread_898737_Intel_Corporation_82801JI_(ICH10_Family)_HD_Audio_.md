---
title: "Intel Corporation 82801JI (ICH10 Family) HD Audio on P5Q mobo"
date: 2008-08-23
forum: Multimedia Software
---

### Post by grigio on 2008-08-23
Is possible to use this card via SPDIF?

        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel



it only works with mplayer directly
mplayer something-ac3.avi -ac hwac3

---

### Post by rockstar08 on 2008-10-08
I am told the latest alsa driver "alsa-driver-1.0.18rc3" will allow you to use spdif on the ich10 soundcard.

You'll have to download and install from source as Intrepid comes with version 1.0.17..

[http://www.alsa-project.org/main/index.php/Download#Developers:_GIT_access](http://www.alsa-project.org/main/index.php/Download#Developers:_GIT_access)

Rockstar..

---

### Post by rfv@gmx.net on 2008-10-08
In my case alsa-driver-1.0.18rc3 is not working. After compiling the sources the alsa mixer shows the IEC958 volumebar but is disabled (muted). When I enable this control the whole sound system hangs. (even kill -9 is not working & soft reboot is not working).

The mobo is an Asus p5q deluxe & Ubuntu 64 server (8.04).

I've found no solution yet. Somebody else??

Suc6 & THX for sharing any idee's

---

### Post by erlguta on 2008-10-31
I have the same sound card in one Dell Studi Slim (540s):
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

It does not works in Intrepid.
Maybe with the release of alsa-1.0.18

Any help would be appreciated.

---

### Post by ouaibe@ouaibe.info on 2008-11-16
I just bought a Dell Studio 540 and the sound card is
*00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller*

It doesn't work at all with alsa under intrepid
I've tried with OSS and I've had to set up again intrepid.

Any help ?
Erlguta, did you succeed with your card (wich is the same ?!)
Did you try alsa-1.0.18 ?

---

### Post by ouaibe@ouaibe.info on 2008-11-17
up

---

### Post by erlguta on 2008-11-20
> **ouaibe@ouaibe.info said:**
> I just bought a Dell Studio 540 and the sound card is
*00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller*

It doesn't work at all with alsa under intrepid
I've tried with OSS and I've had to set up again intrepid.

Any help ?
Erlguta, did you succeed with your card (wich is the same ?!)
Did you try alsa-1.0.18 ?

Yes, and it does not works.
:(
I compiled it with m-a.
Maybe is not yet supported

PD: I have the same Dell

---

### Post by Carcass on 2008-12-27
with the kernel 2.6.28 I known that would be fixed.....is so????? someone known something????

---

### Post by erlguta on 2009-03-20
It seems taht this sound card is working in one Dell Studio Slim putting this line in /etc/modprobe.d/alsa-base:
```

options snd-hda-intel probe_mask=1 model=6stack-dell

```

More info:
[http://ubuntuforums.org/showthread.php?p=6929242](http://ubuntuforums.org/showthread.php?p=6929242)

---

### Post by alex1966 on 2009-04-18
> **erlguta said:**
> It seems taht this sound card is working in one Dell Studio Slim putting this line in /etc/modprobe.d/alsa-base:
```

options snd-hda-intel probe_mask=1 model=6stack-dell

```

More info:
[http://ubuntuforums.org/showthread.php?p=6929242](http://ubuntuforums.org/showthread.php?p=6929242)

I confirm: it works on Dell Studio 540. I just fixed my sound on Debian Lenny.

---

### Post by TechMansoor on 2009-10-19
> **alex1966 said:**
> I confirm: it works on Dell Studio 540. I just fixed my sound on Debian Lenny.

yes I too can confirm. Adding this line does work for the ich10 family of sound cards! :)

Awesome work guys!

I wonder how you figured this out?

---

