---
title: "Sound only sometimes on Gateway 7508gx notebook w/ Conexant AC97."
date: 2008-05-25
forum: Multimedia Software
---

### Post by Ballistixx on 2008-05-25
I am having intermittent sound problems in Hardy Heron. Usually the sound will not work on initial start up (once in a great while it will). If I reboot it usually works (note USUALLY).

My laptop has a Conexant AC97 sound card I believe. I tried all the applicable steps in the comprehensive sound guide and also tried adding the "options snd-intel8x0 ac97_quirk=3" (also tried 0,1,2,4) with no luck.

I am completely stumped. 

If anyone can help me I will be very grateful! Please keep in mind I have only been using Linux for less than a week (any distro) so feel free to talk to me as if I were a child.


Please help.

Kind Regards,
Jason

---

### Post by Ballistixx on 2008-05-27
I ran lspci and dmesg logs when the sound was and wasn't working. I attached the files below. 

I have a feeling my problem has has something to do with my modem and sound card sharing the same pci slot. I tried setting ATI  IXP AC97 as the default sound card with no luck.

*EDITED*-*FIX*- I have come across a solution to move the sound card to another pci slot. Unfortunately I do not have such a luxury since the system is a laptop.

Any ideas???


Regards,
Jason

---

