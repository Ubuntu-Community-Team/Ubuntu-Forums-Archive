---
title: "no sound on laptop asus :(("
date: 2008-05-22
forum: Multimedia Software
---

### Post by djadjana on 2008-05-22
i've just installed ubuntu 8.04 and i'm totally new to all this.
i need help with sound on my Asus A9T (SiS SI7012 AC'97)
i've been through various forums/posts,tried various stuff but - no luck - no sound at all - never had any of sound on ubuntu :(

here's smth for a start

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

find /lib/modules/'uname -r' | grep snd
find: /lib/modules/uname -r: No such file or directory


i've tried adding this
options snd-hda-intel model=lenovo (and auto and few more stuff)
on a bottom of the alsa-base file
but nothing

tried few more things too - no luck :(

can anyone help fix my baby?? :'(

---

### Post by ZorgTheDestroyer on 2008-06-22
Hey I'veexpereienced the same with this onboard sound card . I did the hardware test and suddently I had sound. But not for long Next time I switched on my computer there was no sound again. 

When I try to play .ogg files in VLC I get:
[00000330] pulse audio output error: Failed to connect to server: Invalid argument
[00000330] pulse audio output error: Pulse initialization failed

can anyone help?

---

### Post by Pjotr123 on 2008-06-22
Check this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

---

