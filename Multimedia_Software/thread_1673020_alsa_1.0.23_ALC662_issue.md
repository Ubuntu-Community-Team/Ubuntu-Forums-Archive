---
title: "alsa 1.0.23 ALC662 issue"
date: 2011-01-21
forum: Multimedia Software
---

### Post by anthropo on 2011-01-21
hello, sorry in advance for my english  !

I have a Jetway NC98 Motherboard with lucid server and gnome (for an HTPC). 

I've managed to install hdmi on the nvidia card, works perfectly
```
/etc/modprobe.d/sound.conf : options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
```

BUT i have an issue with the sound on the intel card.
I tried to boot on a lucid livecd (in case it is the changes for the hdmi) but it's natively the same problem.

The sounds seems to come from a tomb when it's set at the middle balance. Nearly can't hear voices, like coming from very far, only music is 'good'.

If balance is set to right or left, sound is clear, but i suspect (trying with test-speaker) it sends the same signal on both sides. My interpretation is that the sound beiing the same, it goes null at the center (1-1==>0)

Could you help me to search a solution

[http://www.alsa-project.org/db/?f=c8fd7b6d33086ccf7d7bea4b8d2cbb30acb9b64d](http://www.alsa-project.org/db/?f=c8fd7b6d33086ccf7d7bea4b8d2cbb30acb9b64d)

thanks in advance

Patrick

---

