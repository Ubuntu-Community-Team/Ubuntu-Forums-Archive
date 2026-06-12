---
title: "Wrap Alsa devices to Oss"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by Almighty Ju on 2007-09-01
Hi all,

What I'm trying to do sounds really simple to me but i just cant get it to work, my sound card is a cmi8788 chip which works fine with the oss driver, what i want to try and do is get alsa to use the oss devices so when i use the gnome-volume-control it uses the oss device through alsa. Then hopefully i can use the volume control buttons on my keyboard

I've looked at google and found out about the oss compatability layer and added the following to /etc/modules.d/aliases which i got from [http://www-old.alsa-project.org/~iwa...Emulation.html](http://www-old.alsa-project.org/~iwa...Emulation.html)
Code:

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

I Hope someone can point me in the right direction or even easier know of a tray icon to control oss and a way to get my keyboard to change it

I posted this in hardware and laptops without realising :oops: can a mod remove that one please.

Thanks,
Julian

---

### Post by zero-9376 on 2007-09-01
have a look in system - preferences - sounds you can set everything to use OSS in there, not sure how that would go with multiple apps trying to share though.
you can also set the mixer device that is controlled by the keyboard/icon tray there just be selecting it

---

### Post by Almighty Ju on 2007-09-03
I've set all the options to oss but the default mixer device box is empty, is that because alsa doesn't support my device?

---

