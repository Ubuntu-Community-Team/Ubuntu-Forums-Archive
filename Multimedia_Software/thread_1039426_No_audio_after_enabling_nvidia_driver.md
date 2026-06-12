---
title: "No audio after enabling nvidia driver"
date: 2009-01-14
forum: Multimedia Software
---

### Post by voteforpedro on 2009-01-14
Please help me...

I edit xorg.conf and specify:

Driver "nv"

I get sound. I specify:

Driver "nvidia"

I get no sound. WHY ON EARTH WOULD THIS HAPPEN?! Why would a driver controlling my PCI-E Nvidia card stop my ON-BOARD INTEGRATED and ENTIRELY SEPARATE audio controller from working?

Chipset is ALC883 and "card" is Intel HDA. Motherboard is ECS A770M-A.

Thanks...

---

### Post by Grumpster on 2009-05-24
That's actually a very good question. I've just come across the same problem. Everything was good till I had a crash. For some reason my nivdia drivers are trying to control my realtek ONBOARD audio. I'd love to know if you found a solution to this one.

---

