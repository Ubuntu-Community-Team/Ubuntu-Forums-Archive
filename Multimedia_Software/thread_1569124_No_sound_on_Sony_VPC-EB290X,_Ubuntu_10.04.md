---
title: "No sound on Sony VPC-EB290X, Ubuntu 10.04"
date: 2010-09-06
forum: Multimedia Software
---

### Post by VirtualWaver on 2010-09-06
Hi all,

As the title says, I have no sound on my laptop. When I first installed Ubuntu 10.04, there were 2 sound outputs in sound preferences (I don't remember exactly what they were, something like HDMI), but no one produces any sound. Then I tried to  upgrade alsa as recommended here -  [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/). After restart my sound worked perfectly. But after few days' daily update my sound disappeared again. But this time there are no sound devices in sound preferences and under "output" I have "Dummy Output". I've tried many solutions listed on this forum and on the web and no solution helped me. I also tried to remove alsa and install open sound as listed here - [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) but still the same results - no audio and audio device. 

Here are some common commands report:

lspci | grep -i audio

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] 

cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug 25 2010 for kernel 2.6.32-24-generic (SM

aplay -l

aplay: device_list:223: no soundcards found...

I tried to add "options snd-hda-intel model=ref" string to /etc/modprobe.d/alsa-base.conf. No luck.

Additionally, I've tried to reinstall pulseaudio:

sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio 

and after that I've got "Waiting  for sound system to respond" when I tried to go into System - Preferences - Sound.

What can I do? 

Thank you in advance.

---

