---
title: "Installing New Video Card for Ubuntu"
date: 2009-02-23
forum: Multimedia Software
---

### Post by Pinejoker on 2009-02-23
I need a help to find a driver or to install my new video card for my linux ubuntu.. PNY Verto Nvidia GeForce 8400 GS PCI . 512 MB DDR2, i need some assistant please.. thank you...

---

### Post by overdrank on 2009-02-23
> **Pinejoker said:**
> I need a help to find a driver or to install my new video card for my linux ubuntu.. PNY Verto Nvidia GeForce 8400 GS PCI . 512 MB DDR2, i need some assistant please.. thank you...

Hi and have you tried under system, administration, hardware drivers?

---

### Post by Pinejoker on 2009-02-23
not yet sir..

---

### Post by Pinejoker on 2009-02-23
what i'm going to do in hardware drivers??

---

### Post by Snypercell on 2009-02-23
when i install this method, how do i adjust the video card performance? i was trying to figure this out the other day, and installed envy over the packaged driver, and had to do a fresh Ubuntu install. i was stuck in low graphics mode.

---

### Post by overdrank on 2009-02-24
> **Snypercell said:**
> when i install this method, how do i adjust the video card performance? i was trying to figure this out the other day, and installed envy over the packaged driver, and had to do a fresh Ubuntu install. i was stuck in low graphics mode.

Ok if you get stuck in low graphics mode you may try the xfix option in recovery mode.
You can boot into recovery mode which is usually the second choice from the grub while booting. Then you should be given 4 options and the last is xfix. When you complete the xfix option then you should be given the choices again and can choose boot normally. 
Then you can use the nvidia settings to adjust the graphics 
```
gksu nvidia-settings
```

---

### Post by Pinejoker on 2009-02-26
> **overdrank said:**
> Ok if you get stuck in low graphics mode you may try the xfix option in recovery mode.
You can boot into recovery mode which is usually the second choice from the grub while booting. Then you should be given 4 options and the last is xfix. When you complete the xfix option then you should be given the choices again and can choose boot normally. 
Then you can use the nvidia settings to adjust the graphics 
```
gksu nvidia-settings
```

Is this correct? 

```
sudo gksu nvidia-settings
```

---

### Post by norwoods on 2009-02-26
use either sudo or gksu:

gksu nvidia-settings

sudo nvidia-settings

---

### Post by Pinejoker on 2009-02-27
This problem is solved. =) thanks guys

---

