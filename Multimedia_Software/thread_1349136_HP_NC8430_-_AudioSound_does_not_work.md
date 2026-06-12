---
title: "HP NC8430 - Audio/Sound does not work"
date: 2009-12-07
forum: Multimedia Software
---

### Post by nokia9300 on 2009-12-07
Since I upgraded to ubuntu 9.10 my sound does not work. in 8.10 & 9.04 it used to work on the headphone jack.

I downloaded the latest alsa-drivers from alsa-project and compiled and installed it successfully. No mater what I do - I cant get it to work.

Also made sure that I have the latest version of BIOS from HP updated.

Below link is my system profile with all details related to alsa.

[http://www.alsa-project.org/db/?f=02d6f41056fca1bb3bd136e8238548ec300f1368](http://www.alsa-project.org/db/?f=02d6f41056fca1bb3bd136e8238548ec300f1368)

Please help!!!

Thanks in advance.

---

### Post by ambo on 2009-12-09
I am also having trouble with the sound on exactly the same hardware.

I found [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568) and I did the force-reload and the sound started working.

There were however numerous errors and this lead me to [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/267963](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/267963).

I'm unsure if I've actually solved the problem but it seems to be working for now. :)

---

### Post by nokia9300 on 2009-12-09
Thanks ambo for your reply.

I did come across that post and tried force-loading the modules and all that good stuff. The volume is only working on the headset and when I use the docking station. However, the laptop speaker was not working.

I took the bull by the horn and disassambled the laptop to find out that the speakers in my laptop was bad. Nothing to do with the drivers I was loading.

Time for a new laptop I guess :).

For those of you having this issue - I am documenting future reference - these options have worked for me when I changed in 


/etc/modprobe.d/alsa-base.conf

Added the below options

options snd-hda-intel model=hp-bpc
options snd-hda-intel enable=1 index=0
options snd-hda-intel enable_msi=1

(Note: I guess you can send the above options in a single line something like
"options snd-hda-intel enable=1 index=1 enable_msi=1 model=hp-bpc" with out the quotes.
Since I was troubleshooting - I tried to load one option at a tiem and started testing.)

---

