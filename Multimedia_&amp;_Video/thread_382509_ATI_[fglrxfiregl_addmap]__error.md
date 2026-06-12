---
title: "ATI [fglrx:firegl_addmap]  error"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by nabdan on 2007-03-12
Hi all,

I have some problem with my ATI card.

I have tested everything but I have bad performances in 3d.

Manually or using Envy, every time the same problem:

All seems to point this error:

```

 nab@nab-desktop:~$ dmesg | grep fglrx
[17179615.832000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[17179615.832000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
**[COLOR="Red"][17179617.188000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)[/COLOR]**
[17179617.188000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[17179617.196000] [fglrx] total      GART = 130023424
[17179617.196000] [fglrx] free       GART = 114032640
[17179617.196000] [fglrx] max single GART = 114032640
[17179617.196000] [fglrx] total      LFB  = 268304384
[17179617.196000] [fglrx] free       LFB  = 250474496
[17179617.196000] [fglrx] max single LFB  = 250474496
[17179617.196000] [fglrx] total      Inv  = 0
[17179617.196000] [fglrx] free       Inv  = 0
[17179617.196000] [fglrx] max single Inv  = 0
[17179617.196000] [fglrx] total      TIM  = 0

```


All seems work, but really bad performances in 3D.

Please help :)

Bye !

---

