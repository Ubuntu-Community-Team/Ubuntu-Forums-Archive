---
title: "GeForce 6200....should I install the included drivers?"
date: 2009-04-25
forum: Multimedia Software
---

### Post by mudman00 on 2009-04-25
Hello, I have just installed a new video cared and it seems to be working quite well. The old card, really old by many of your standards I am sure, was a GeForce 5700.......the new card is the super fast (just kidding here) GeForce 6200............I don't play video games or use any video intensive software so I just don't need anything better. My primary objective is system stability and getting as many miles as I am able out of the hardware.

My question is, should I install the drivers that came with the card? Are there any advantages to doing so? Are there any disadvantages? And, the most important, will it affect system stability? I don't want to put any drivers or apps on the system that Ubuntu32 8:10 doesn't like.

Please keep in mind that I am still new to this. I have only been in the Linux world for a little over a month now and don't have the time that I need to be able to devote to learning things more quickly than I am.

I don't know if it makes any difference, but I am running an ASUS A7N8X-X with a gig of Corsair ram......I built the box about five years ago and the video card finally went belly up, so I got a new one yesterday.

Thank you for any and all help, suggestions or comments.

Craig

---

### Post by psyke83 on 2009-04-25
> **mudman00 said:**
> Hello, I have just installed a new video cared and it seems to be working quite well. The old card, really old by many of your standards I am sure, was a GeForce 5700.......the new card is the super fast (just kidding here) GeForce 6200............I don't play video games or use any video intensive software so I just don't need anything better. My primary objective is system stability and getting as many miles as I am able out of the hardware.

My question is, should I install the drivers that came with the card? Are there any advantages to doing so? Are there any disadvantages? And, the most important, will it affect system stability? I don't want to put any drivers or apps on the system that Ubuntu32 8:10 doesn't like.

Please keep in mind that I am still new to this. I have only been in the Linux world for a little over a month now and don't have the time that I need to be able to devote to learning things more quickly than I am.

I don't know if it makes any difference, but I am running an ASUS A7N8X-X with a gig of Corsair ram......I built the box about five years ago and the video card finally went belly up, so I got a new one yesterday.

Thank you for any and all help, suggestions or comments.

Craig

No NVIDIA retail driver CD ever included a Linux driver as far as I know, so it would be impossible to do what you propose.

Use the "Restricted Drivers Manager" (or "Hardware Manager") in the System/Administration menu. This application will automatically fetch and install the appropriate driver for your card.

Don't try to do it another way (e.g. installing from the tarball on the nvidia.com site), or else you'll have issues when upgrading kernels or distributions.

---

