---
title: "hda intel pch speaker not working but headphones work great"
date: 2015-03-17
forum: Multimedia Software
---

### Post by mbcastro on 2015-03-17
I've just installed Ubuntu 14.10 on a HP EliteOne 800 G1 All-in-one desktop.
Everything works great (mic, headphones, camera) except the internal speakers.

I'm sure that the speaker is not muted. However, in alsamixer, there is a speaker column but there is no "volume bar" on it, which is pretty weird.
The sceen shot is here: [https://www.dropbox.com/s/89v1akqoqh6bmjo/Screenshot%20from%202015-03-17%2015%3A54%3A36.png?dl=0](https://www.dropbox.com/s/89v1akqoqh6bmjo/Screenshot%20from%202015-03-17%2015%3A54%3A36.png?dl=0)

Here you can find the information obtained from ALSA Information Script v 0.4.64:

[http://www.alsa-project.org/db/?f=40ae401b7d2ee064a6c82cce75b0107319233d11](http://www.alsa-project.org/db/?f=40ae401b7d2ee064a6c82cce75b0107319233d11)

Does anyone could help me fixing it?

Thank you in advance.

---

### Post by dino99 on 2015-03-18
install 'pavucontrol', then select the good 'output device'; you may also tweak the 'config' tab settings first

---

### Post by mbcastro on 2015-03-18
Hi,

I've already installed pavucontrol and selected the correct output device ("analog stereo output").
When I play a sound I can see in pavucontrol the sound bar going "up and down", which indicates that I'm playing a sound.
However, nothing goes out of the speakers.

Any idea?

---

### Post by mbcastro on 2015-03-18
Hi,

I've just figured out how to solve my problem: I had to upgrade the alsa driver to the latest version.
I followed this wiki: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

