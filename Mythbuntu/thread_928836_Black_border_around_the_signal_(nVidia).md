---
title: "Black border around the signal (nVidia)"
date: 2008-09-24
forum: Mythbuntu
---

### Post by Ransak on 2008-09-24
Hi,

I'm using a GeForce FX 5500 PCI video card in my new mythtv box and outputting via S-video out to S-video in on my Panasonic 42" plasma TV. Thus far the quality has been good recording and playing standard definition from my cable provider. I'm using the nVidia proprietary driver on Mythbuntu 8.0.4.

My only complaint at this point is a one inch black border around the output signal. My TV shows a resolution of 1024x768 in the specifications, so I have a feeling the S-video out on my nVidia card isn't outputting at that resolution, but that's just a guess. I've tried tweaking the resolution in X but it doesn't seem to help. The border is there even at post, so I'm afraid it might be a hardware limitation.

Has anyone else ran into this? Was it resolvable?

---

### Post by tgm4883 on 2008-09-24
> **Ransak said:**
> Hi,

I'm using a GeForce FX 5500 PCI video card in my new mythtv box and outputting via S-video out to S-video in on my Panasonic 42" plasma TV. Thus far the quality has been good recording and playing standard definition from my cable provider. I'm using the nVidia proprietary driver on Mythbuntu 8.0.4.

My only complaint at this point is a one inch black border around the output signal. My TV shows a resolution of 1024x768 in the specifications, so I have a feeling the S-video out on my nVidia card isn't outputting at that resolution, but that's just a guess. I've tried tweaking the resolution in X but it doesn't seem to help. The border is there even at post, so I'm afraid it might be a hardware limitation.

Has anyone else ran into this? Was it resolvable?

You need to adjust your overscan settings in nvidia-settings

---

### Post by Ransak on 2008-09-24
> **tgm4883 said:**
> You need to adjust your overscan settings in nvidia-settings

That's a proprietary package, right? I'll give it a shot tonight and post back the results. Thanks!

---

### Post by Ransak on 2008-09-25
I installed the nividia-settings package and upped my overscan to 15. Now the border is gone! Thanks!

---

