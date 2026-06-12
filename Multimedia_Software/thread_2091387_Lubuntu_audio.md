---
title: "Lubuntu audio"
date: 2012-12-05
forum: Multimedia Software
---

### Post by Fabienux on 2012-12-05
Hi everybody,

I know that this point has been discussed several time, but after having tried all the proposed solutions without success and re-install a couple of time lubuntu, I really need help from linuxian experts.

the problems : 

1) the integrated micro does not work (gmail videochat, guvcview, ...) and I already tried all the possible alsamixer configurations. In some configurations (internal micro I think), I got a kind of background sizzle but nothing sensible to my voice or any external sounds.

2) the integrated speakers work correctly but, when I plug headsets or external speakers there is no sound. 

all the info are here :
[http://www.alsa-project.org/db/?f=fc12dba7cccc9fa4b144a25effe76933fd737d7a]("http://www.alsa-project.org/db/?f=fc12dba7cccc9fa4b144a25effe76933fd737d7a")

Thanks for your help

Cheers
Fabien

---

### Post by Fabienux on 2012-12-06
Seriously? no one knows?

---

### Post by Fabienux on 2012-12-09
?

---

### Post by BicyclerBoy on 2012-12-09
You could try adding this to /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel index=0 model=toshiba position_fix=1
(this worked with old ver alsa 1.0.21, some or all of it could now be automatic)

Reboot then run alsamixer(gui) & select capture devices & set recording level to 40% & then all mic boost to max.

May need to un-boost one mic to reduce background noise.

Try using pavucontrol to set/adjust...this has a VU meter to monitor audio.

---

### Post by Fabienux on 2012-12-09
Hi BicyclerBoy

thanks for trying to help me, I did what you suggested but unfortunately without success. I keep this background noise (whatever the recording level) and the micro remains totally insensible to external noises, I mean, the monitor remains at the same noise level and doesn't increase when I speak, even loudly and close to the micro.

---

### Post by BicyclerBoy on 2012-12-11
Do you have multiple microphones listed?
Can you change the mic boost ?
Can you change any line input to mic?

It is common for laptops/netbooks to have mixed up inputs/outputs because they are non-standard & have incorrect BIOS tables.

---

### Post by Fabienux on 2012-12-15
Hi BicyclerBoy,

I have 2 columns Internal M, 1 Digital, 2 Mic Boost and 1 Capture  

the screenshot below show you my alsamixer on F5 with everything in it.

---

### Post by Fabienux on 2012-12-15
alsamixer...

---

### Post by BicyclerBoy on 2012-12-15
Re: headphones problem
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/988098](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/988098)

Using pavucontrol can you set the port to speaker (from headphone)?

Don't know about microphone..do you have an ext mic input?
My netbook has common connector for headphones & ext mic.
Maybe your connected headphones are acting like insensitive mics?
Try yelling into the headphone drivers (transducer)..

---

