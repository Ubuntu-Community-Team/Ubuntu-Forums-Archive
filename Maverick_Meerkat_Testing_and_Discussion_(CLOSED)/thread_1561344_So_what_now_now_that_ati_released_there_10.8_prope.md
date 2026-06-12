---
title: "So what now now that ati released there 10.8 properiety drivers?"
date: 2010-08-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-08-26
Is there going to be a new fglrx driver any time soon that is about to appear in jockey? Because the new fglrx-installer that i found in x-swat ppa didn't worked so well and i had to remove it via apt-get remove fglrx command.

Thanks in advance.

---

### Post by xir_ on 2010-08-26
> **aviramof said:**
> Is there going to be a new fglrx driver any time soon that is about to appear in jockey? Because the new fglrx-installer that i found in x-swat ppa didn't worked so well and i had to remove it via apt-get remove fglrx command.

Thanks in advance.


The new driver is not x server 1.9 compatible. There would be no point uploading it into the repos

We will have to wait at least another month for a new driver to see if they can get it working.

---

### Post by aviramof on 2010-08-26
I have to say that this is very dissapointing because it mean one more month without compiz.

---

### Post by jfernyhough on 2010-08-26
Complain to AMD/ATi! :D

---

### Post by aviramof on 2010-08-26
I think i'll just try to downgrade to xserver 1.8 and that it.

---

### Post by ktp on 2010-08-26
there's usually "beta" version that ubuntu comes with it's Beta release...at least that's how it's work past few releases since ATI's released version is always behind what Ubuntu ships with.  That being said, I can't say (since I don't know) if this will happen this time.

---

### Post by xir_ on 2010-08-27
> **aviramof said:**
> I have to say that this is very dissapointing because it mean one more month without compiz.

Are you an evergreen user? As most cards have compositing out of the box, via the open source drivers. It's just power management that's really lacking these days.

---

### Post by coffeecat on 2010-08-27
> **aviramof said:**
> I have to say that this is very dissapointing because it mean one more month without compiz.

Compiz works just fine with the open-source driver in Maverick with my ATI Radeon HD4200 graphics. I know this won't be so with some ATI cards, but have you tried the OS driver?

---

### Post by aviramof on 2010-08-27
Yes i am currently using xorg and xserver and not fglrx and it doesn't work with my ati HD3650 512MB DDR2 card.

---

### Post by muximus on 2010-08-27
i think they mean try the xserver-xorg-video-ati driver ... u would be using xserver and xorg anyways...

---

### Post by aviramof on 2010-08-28
I do use xserver-xorg-video-ati or at least he is installed.

---

