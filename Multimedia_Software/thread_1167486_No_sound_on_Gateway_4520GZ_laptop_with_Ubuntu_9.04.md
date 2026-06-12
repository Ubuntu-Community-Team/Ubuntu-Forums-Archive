---
title: "No sound on Gateway 4520GZ laptop with Ubuntu 9.04"
date: 2009-05-22
forum: Multimedia Software
---

### Post by mrs1179 on 2009-05-22
I'm new to Linux and have not been able to get my sound to work.  I have a 5-year old Gateway 4520GZ laptop and installed Ubuntu 9.04.  I have been working through the steps in _[[U][FONT=Arial][SIZE=2][COLOR=#0000ff]https://help.ubuntu.com/community/SoundTroubleshooting[/COLOR][/SIZE][/FONT]_]("https://help.ubuntu.com/community/SoundTroubleshooting")[/U] but have been unable to find a solution.  Stepping through the document, I did the following:

The results of "aplay -l" are:
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When I run "sudo aptitude install linux-ubuntu--modules-`uname -r` linux-generic", it looks like it does not install anything, because I get this message:
Couldn't find any package whose name or description matched "linux-ubuntu--modules-2.6.28-11-generic"

The result of "lspci -v" says that my Kernel module is snd-intel8xo.

My ALSA information is downloaded to [http://www.alsa-project.org/db/?f=56e99094a3bb43dee63d8cefc577816f3616b973](http://www.alsa-project.org/db/?f=56e99094a3bb43dee63d8cefc577816f3616b973)

When I look for Codec information, I do not see anything that looks like what is in the SoundTroubleshooting document.  I see a section called "AC97 Codec Information" , but there is no line titled "Codec:" 

At this point, I'm lost.  Does anyone have an idea on where I can proceed from here?

I did find a paragraph near the end of the SoundTroubleshooting document from webbca01 that references adding options to alsa-base.conf for the snd-intel8xo.

I tried his solution and added this: "options snd-intel8x0 ac97_quirk=3", but it did not do anything.

Any ideas would be greatly appreciated.

[]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

