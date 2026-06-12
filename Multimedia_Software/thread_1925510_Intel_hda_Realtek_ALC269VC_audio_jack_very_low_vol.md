---
title: "Intel hda Realtek ALC269VC audio jack very low volume/not working"
date: 2012-02-14
forum: Multimedia Software
---

### Post by micschk on 2012-02-14
I have a Samsung laptop with Ubuntu 11.10 64 bit installed and cannot seem to get the audio card to work properly; internal speakers work just fine but when I plug in my headphones the speakers don't get muted. If I select the headphones as output in the volume panel, the internal speakers are muted but the headphones only have a very faint sound (barely noticeable).

I have tried a lot of the "options snd-hda-intel model=xyz" in /etc/modprobe.d/alsa-base.conf; basic, quanta, laptop-amic, samsung, auto, laptop, laptop-eapd, +ultra, samsung, samsung-p50, mobile

Of these, "samsung" works reasonably with kernel 3.0, but not with 3.2 or 3.3 that I'd like to run because of the trackpad & i5 processor...

Output of the ALSA information script; [http://www.alsa-project.org/db/?f=922fb1e561ddc93cedad4ef26aa1599acdca02ae](http://www.alsa-project.org/db/?f=922fb1e561ddc93cedad4ef26aa1599acdca02ae)

---

### Post by Nmil on 2012-05-01
Hi,

I actually have the same problem, although this is for a fresh install of 32 bit Precise Pangolin on my Samsung Series 7 laptop. Did you find a solution ?  My alsa-info is there :

  [http://www.alsa-project.org/db/?f=9de24f14309c614f9c7e5fa487f73a24cfd64afd](http://www.alsa-project.org/db/?f=9de24f14309c614f9c7e5fa487f73a24cfd64afd)

---

### Post by micschk on 2012-05-01
Nope... I'm using an external (USB) soundcard for the time being.

---

### Post by Nmil on 2012-05-04
Ok, I posted a bug report and got a working workaround that will do until the bug is actually fixed (hopefully). 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/992644](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/992644)

---

