---
title: "Kubuntu 14.04 Fresh install Sound issues."
date: 2014-06-15
forum: Multimedia Software
---

### Post by Jenopo on 2014-06-15
So I've just installed Kubuntu 14.04 alongside Windows 8.1 on my computer (HP Envy M6) and have been having sounds problems;

First, it would play sound but turning the sound up and down had no effect and it was fairly quiet.

However, I've since restarted it and now the sound is completely silent no matter what the volume setting is. Any ideas?

EDIT: Got the sound back through the KDE Mixer, but the volume control still has no effect.

EDIT 2: I've totally fixed it, I just had to set my Alsa Playback as the master channel, apologies for wasting anyone's time. 

MY fix was to simply right 

1)open kmix in the corner, 

2)see which vollume bar actually affected the volume, 

3)click away and then right click it

4) Select "Select Master Channel" and set it to the functioning volume channel. 

I'll attach screenshots if you think it will help.

---

### Post by xc3RnbFO8P on 2014-06-16
> **Jenopo said:**
> So I've just installed Kubuntu 14.04 alongside Windows 8.1 on my computer (HP Envy M6) and have been having sounds problems;

First, it would play sound but turning the sound up and down had no effect and it was fairly quiet.

However, I've since restarted it and now the sound is completely silent no matter what the volume setting is.

**My laptop marketed itself on it's use of Beats  by Dre Speakers**, and I suspect there may be some kind of driver issue, does anyone have any ideas?

Do you mean connected to bluetooth ?

---

### Post by Jenopo on 2014-06-16
I really didn;t make that clear heh. No, the speakers are built in, and are, as a far as I can tell, the only speakers. 

However, I tried my external speaker earlier, and there was still no sound from that, so I don;t think the speakers are the problem, is that any help?

---

### Post by xc3RnbFO8P on 2014-06-16
1 ) Right click on the speaker icon > choose mixer > settings select master channel 

2 ) Right click on the speaker icon > choose mixer > audio setup (what options do have)

I am using bluetooth at the moment otherwise I use **built in audio analog**

---

### Post by Jenopo on 2014-06-16
Thanks for the screenshots, that was my fix too. Forgive my noobishness.

---

### Post by xc3RnbFO8P on 2014-06-16
Nothing to forgive  I'm glad I could help :)

---

### Post by Bucky Ball on 2014-06-16
*Thread moved to **Multimedia & Video**.*

---

### Post by Yellow Pasque on 2014-06-16
I'm confused. Is there still a problem here? If not, please mark the thread solved (thread tools menu towards top).

If there is still an issue, please clarify, and give info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

