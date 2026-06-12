---
title: "no sound through headphones jack"
date: 2012-01-12
forum: Multimedia Software
---

### Post by zaibotrenktas on 2012-01-12
Hello,

I tried various solutions which I found on the internet, but nothing helps.

I have ASUS N73Jn laptop.

The problem is that then I put headphones or external speakers there is no sound, unless I manually open Mixer and unmute 'Master' and raise sound level of 'Speaker'.

Here's a link to picture how my Mixer settings look before and after the jack is plugged: [http://dl.dropbox.com/u/36902762/Screenshot%20-%20120112%20-%2011%3A37%3A18.png]("http://dl.dropbox.com/u/36902762/Screenshot%20-%20120112%20-%2011%3A37%3A18.png")

---

### Post by zaibotrenktas on 2012-01-13
bump..

---

### Post by Toz on 2012-01-13
Have you tried this: [http://justcheckingonall.wordpress.com/2011/03/09/no-sound-on-headphones-with-intel-hda-3400realtek-alc259-in-linux/]("http://justcheckingonall.wordpress.com/2011/03/09/no-sound-on-headphones-with-intel-hda-3400realtek-alc259-in-linux/")?

---

### Post by MoreOrLess on 2012-01-13
> **Toz said:**
> Have you tried this: [http://justcheckingonall.wordpress.com/2011/03/09/no-sound-on-headphones-with-intel-hda-3400realtek-alc259-in-linux/]("http://justcheckingonall.wordpress.com/2011/03/09/no-sound-on-headphones-with-intel-hda-3400realtek-alc259-in-linux/")?
That's for a different model. It may have the same codec and subsequently, the same solution, but let's double-check the alsa info first:

@OP: Do this - [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by iip on 2012-01-13
I have similar problem after adding alsa-hda-dkms from ppa:ubuntu-audio-dev/alsa-daily, but it is ok now, in the "option" tab, there is option "Independent HP", I switch it to "OFF", now the sound is perfect, speaker automatically silent when headset is plug in, everything normal now :D

My laptop is ASUS K40ij

---

### Post by zaibotrenktas on 2012-01-14
> **iip said:**
> I have similar problem after adding alsa-hda-dkms from ppa:ubuntu-audio-dev/alsa-daily, but it is ok now, in the "option" tab, there is option "Independent HP", I switch it to "OFF", now the sound is perfect, speaker automatically silent when headset is plug in, everything normal now :D

My laptop is ASUS K40ij

Thank you! It works like a charm.

As a new Linux user I really appreciate the help of the community. I hope that soon I'll be able to help people, too. ;)

---

