---
title: "video card switches between /dev/video1 and video0"
date: 2010-02-03
forum: Multimedia Software
---

### Post by mantorpcity on 2010-02-03
Seemingly at random when I reboot my PC which I do every now and then, when I get it back up and running it will sometimes have switched my video card from using /dev/video1 to /dev/video0 or vice versa. It's not a huge deal but it is slightly annoying and I would like to understand why it does it and how I can stop it from flip flopping. 

Not sure what you need to know in order to answer but I use 9.10, gnome 2.28.1, the video card is a Hauppauge 150 PVR something.

Thanks much

---

### Post by mantorpcity on 2010-02-26
Hmm, it just did it again. Does anyone know what logic if any is used to determine what makes the videocard appear as /dev/video0 instead of /dev/video1 ?

---

### Post by sisco311 on 2010-02-26
Instead of /dev/video* use the static device names in /dev/v4l/by-path/*.

---

### Post by mantorpcity on 2010-02-26
> **sisco311 said:**
> Instead of /dev/video* use the static device names in /dev/v4l/by-path/*.

Thanks that works. Much appreciated.

---

