---
title: "poss answer to my sound issue"
date: 2012-05-18
forum: Multimedia Software
---

### Post by wonderingwhy on 2012-05-18
So I'm using ubuntu 10.04 and I have a Hauppauge WinTV HVR 4000 card. I'm having problems with getting sound from TV when using Kaffeine. Although sound in all other respects is fine - and I can record TV from Kaffeine and play back through VLC with no probs but not through Kaffeine.

This could be the possible answer:

> Sound driver

Alsa driver: cx88_alsa.

To make sure the sound card in the HVR-4000 does not grab card index 0 (instead of your motherboard or discrete sound card) add the following to /etc/modprobe.d/alsa-base (or wherever your distro sets alsa kernel module options):

[QUOTE]# Prevent abnormal drivers from grabbing index 0
options cx88_alsa index=-2
[/QUOTE]

So my question is how do I locate where my distro sets alsa kernel module options?

Many thanks

---

### Post by enigma32 on 2012-05-18
I'm running 10.04 too.

I think this is the file you're looking for:
/etc/modprobe.d/alsa-base.conf

---

### Post by wonderingwhy on 2012-05-20
Hey Enigma32

Thanks so much for that, I already had that loaded so this isn't my problem. Back to the drawing board.

---

