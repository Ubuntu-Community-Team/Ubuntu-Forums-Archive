---
title: "No sound. How to completely remove OSS"
date: 2011-03-08
forum: Multimedia Software
---

### Post by atentik on 2011-03-08
Few days ago the sound from my lenovo x61 started messing up so I did few googling and came up with solution to replace my pulseaudio with oss. Well, I following the instruction and now my sound stopped working altogether. Any help will be real helpful. 
> aplay -l
**** List of PLAYBACK Hardware Devices ****
aplay: device_list:256: snd_ctl_pcm_next_device

and here is my alsa [file]("http://www.alsa-project.org/db/?f=0daedfd505eb6bac5951be46ebb04715ae74d1e0")...

---

### Post by atentik on 2011-03-09
Thanks for the help... problem solved by shutting down the computer for few minutes and rebooting. My problem now is to get the internal microphone to work. It used to work but has now stopped working altogether. I have Lenovo X61 table. 

Thanks.

---

### Post by Yellow Pasque on 2011-03-09
Make sure it's not muted in alsamixer.

---

