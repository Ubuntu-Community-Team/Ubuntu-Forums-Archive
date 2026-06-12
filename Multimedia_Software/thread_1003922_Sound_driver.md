---
title: "Sound driver"
date: 2008-12-06
forum: Multimedia Software
---

### Post by Merps on 2008-12-06
Hey I am runnning a variant of ubuntu 7.04 : Compiz Fusion 1.0, but my audio card is not commonly used and not working at the moment (Via VT1618 codec on the VT8237R South Bridge Chipset on the Core fusion board).  Is there a way to try and install it with say Alsa config?

---

### Post by Merps on 2008-12-06
OK I found this here

[http://osdir.com/ml/ubuntu.devel.kernel.general/2006-04/msg00031.html](http://osdir.com/ml/ubuntu.devel.kernel.general/2006-04/msg00031.html)

which indicates:

Subject: [PATCH] [UBUNTU:sound/pci/] Add various models to ALSA supported list

The above commits by Takashi Iwai from various authors add support for:
    - VIA VT1618 codec

Signed-off-by: Daniel T Chen <crimsun@xxxxxxxxxx> Dated early 2006


So it seems that it is possible to get audio for VIA VT1618 codec with ALSA ubuntu, I jusy don't know how to install ALSA?

I tried sudo alsaconfig but command not recognised.

---

### Post by Merps on 2008-12-06
Ok more progress:

From a poster on a forum "Halfconscious":

I have unmuted IEC958 using alsamixer or amixer. I have spent many hours searching for solutions.

Currently using Ubuntu 7.04 with homebuilt 2.6.22.10

....

then same poster wrote later:

I've just got it working!
It actually works when I use default device - not iec958

e.g. aplay -D default xxx.wav


So the solution is to install alsa first, then to use default device?  However I don't know how to do these two things?

---

### Post by Merps on 2008-12-06
I scanned the wiki help file here [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

and from it, I tried this:

sudo apt-get install alsa-oss

Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alsa-oss has no installation candidate

but you can see it failed.

---

### Post by Merps on 2008-12-06
ok also went to the system --> preferences --> sound

and noticed that the

sound events
music and movies
audio conferencing
default mixer tracks

all have drop down menus that include ALSA, ESD, OSS, and an option for the Via Chipset of the board I am on at the moment, the 8237.

That said, none of them seemed to get anything from my speakers, and the test always fails.  Is there a mute to check somewhere?

---

### Post by Merps on 2008-12-06
ok in term --> alsamixer runs, checked all channels were 00 not MM, then tried OSS and ALSA again, still no audio and all the tests don't work.

From here: [https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

checked volume at top right hand of screen, volume @ 80% it does say OSS not ALSA though.

aplay -l
**** List of PLAYBACK Hardware Devices ****
aplay: device_list:213: control open (0): Permission denied

need to be root for that i presume.


find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.20-17-generic/kernel/ubuntu/misc/snd-bt-sco.ko
/lib/modules/2.6.20-17-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.20-17-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.20-17-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.20-17-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.20-17-generic/kernel/sound/pci/snd-ens1370.ko
... and it goes on for a while so no problem


my sound card is supported by ALSA
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-VIA](http://www.alsa-project.org/main/index.php/Matrix:Vendor-VIA)


"Once you've done the basic troubleshooting listed above, if things still aren't working, you may have found a bug in Ubuntu."

Really?  How strange

---

### Post by Merps on 2008-12-10
ok I need help as this is one of the few distros that works fast enough to use on 1 core cpu systems.

any other suggestions about getting sound to unmute with this distro or is it a more generic problem?  anyone recommend not wasting sleep and just using it without sound?

---

