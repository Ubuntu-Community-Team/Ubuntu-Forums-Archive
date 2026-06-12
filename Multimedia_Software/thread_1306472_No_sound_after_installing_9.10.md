---
title: "No sound after installing 9.10"
date: 2009-10-30
forum: Multimedia Software
---

### Post by PeddyOfficer on 2009-10-30
Hi

I've been trying numerous tips from similar threads in this forum, but nothing seems to help.

I have sound running 'speaker-test' in terminal and also using System-->Preferences-->Multimedia Systems Selector (Plugin: Alsa, Device: ALC662 rev1 Analog).

There is no devices under "Hardware" in Sound Preferences. Under "Output" I have "Dummy Output (Stereo)". Under "Applications" I can see what programs are playing sound (i.e. Totem, Rythmbox).

In alsamixer I can see it's using HDA Intel as card (which is correct). However, I cannot alter the volume level for headphones and speakers. Both are set to zero. I've tried running alsamixer both as user and sudo. No luck. I can change volume level for Master and PCM.

Any suggestions?

EDIT: I found out I have sound on YouTube and anything else using flash, but not Totem, Rythmbox, VLC etc.

Thank you.

---

### Post by Ulysses361 on 2009-10-30
Please try this solution:

[https://answers.launchpad.net/ubuntu/+source/sl-modem/+question/87045](https://answers.launchpad.net/ubuntu/+source/sl-modem/+question/87045)

---

### Post by PeddyOfficer on 2009-10-30
Spot on! 

Thank you.

---

