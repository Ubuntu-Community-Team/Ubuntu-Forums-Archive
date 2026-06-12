---
title: "785GT-E63 setting up sound."
date: 2010-12-20
forum: Multimedia Software
---

### Post by tritron on 2010-12-20
I just got msi 785GT-E63 and installed  nvidia 220.
I had added  to alsa-base.conf 
options snd-hda-intel model=6stack
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
I setup asound.conf to look like this 
pcm.!default {
type hw
card 1
device 7
}
This gives me sound using hdmi on nvidia card.
Now on mythtv channel change it plays  last bit of sound over and over so it makes noise, is there a way to stop it.
I wonder if someone can point me on setting asound to out put to hdmi and digital out at the same time.

---

