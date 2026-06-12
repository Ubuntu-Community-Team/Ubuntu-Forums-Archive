---
title: "Changing Line in jack to rear out"
date: 2009-06-22
forum: Multimedia Software
---

### Post by boxy240 on 2009-06-22
Well I'm trying to change my line in jack on my built in sound card so it works as the Rear out jack so I am able to use my surround sound, I haven't got the slightest clue what to do, and I'm new to Linux so if possible can I have something really easy to follow please, I am using Ubuntu 9.04 and have the  Realtek ALC883 built into my motherboard. Currently my sound works fine on the front 2 speakers but I miss having my surround sound

Thanks in advance

---

### Post by raboofje on 2009-06-22
> **boxy240 said:**
> I'm trying to change my line in jack on my built in sound card so it works as the Rear out jack so I am able to use my surround sound

Are you sure this is physically possible? i.e., that your sound card supports this at all?

---

### Post by boxy240 on 2009-06-22
yep 100% I use it in my vista and xp boot

---

### Post by raboofje on 2009-06-22
That sure is a neat feature. 

Perhaps 'gnome-alsamixer' provides a way to switch between 'input' and 'output' modes?

If not, perhaps switching the 'model' parameter of the snd-hda-intel module by modifying /etc/modprobe.d/alsa-base as documented at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) ?

---

