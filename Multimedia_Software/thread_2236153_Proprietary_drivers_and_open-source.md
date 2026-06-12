---
title: "Proprietary drivers and open-source"
date: 2014-07-24
forum: Multimedia Software
---

### Post by renanrischiotto1 on 2014-07-24
Good evening! 

How is the performance of the Nouveau in recent 3.15 and 3.16 kernels compared to proprietary drivers NVIDIA? I use Xubuntu, makes a difference than using Ubuntu?

Sorry if my english is bad, I'm brazilian, Google Translator helps me :)

Hugs!

---

### Post by silvio.alencar on 2014-07-25
nvidia-prime with most up-to-date drivers > nvidia-prime 331.38 from canonical partners > bumblebee > nouveau

as far as I remember Nouveau mainly promises giving proper 2D support.

I expect some brazilian portuguese won't hurt ;)
Opa tudo bom? Sou brasileiro também.

Two days ago I posted a thread regarding nvidia-proprietary drivers right here.
[http://ubuntuforums.org/showthread.php?t=2235859](http://ubuntuforums.org/showthread.php?t=2235859)

The performance changes A LOT. I still will do a benchmark comparing Street Fighter vs Tekken benchmark scores + FPS to assess an empiric evaluation. I'm first going to try the difference between xorg-edgers and ~marmeley ppas because some games that were working before (Injustice: God Among Us for example) have stopped. It seems my problem was render thread related to gstream and xorg provide extra packages rather than only the clean driver.

---

### Post by Yellow Pasque on 2014-07-25
It depends on what GPU you have.

---

### Post by Yellow Pasque on 2014-07-28
[http://www.phoronix.com/scan.php?page=article&item=nvidia_nouveau_linux316&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_nouveau_linux316&num=1)

---

