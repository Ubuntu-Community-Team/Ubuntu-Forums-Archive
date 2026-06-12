---
title: "Guys !!! No Sound !!!"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by taurusx5 on 2008-02-09
Guys !!! Just ofr your info, I got Ubuntu 7.10 installed on my Gateway M210S... Ever since I installed ubuntu a month ago, I don't have any sound. What must I do to get sound? Thanks!

---

### Post by xc3RnbFO8P on 2008-02-10
Check this out:
> [http://ubuntuforums.org/showthread.php?t=614903](http://ubuntuforums.org/showthread.php?t=614903)

Post #5

Download:

alsa-driver-1.0.16rc1.tar.bz2
alsa-lib-1.0.16rc1.tar.bz2
alsa-utils-1.0.16rc1.tar.bz2

and change 1.0.15rc1.... to 1.0.16rc1....

---

### Post by taurusx5 on 2008-02-12
Ringi, thank you so much for your response. I have 2 questions. 1) When you said to change 1.0.15rc1  to 1.0.16rc1, what file must I do that to? So far, going to the webpage to download the files, I only see files that start with 1.016rc1 and not 1.015rc1. 2)  Will the thread that you provided the link for be a solution with any sound card? Keep in mind that I have a motherboard with integrated sound card... Thanks...

---

### Post by xc3RnbFO8P on 2008-02-13
First try this:

> sudo aptitude install linux-backports-modules-generic

---

