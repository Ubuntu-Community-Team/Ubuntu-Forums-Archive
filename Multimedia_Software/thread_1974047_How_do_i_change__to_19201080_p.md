---
title: "How do i change  to 1920*1080 p?"
date: 2012-05-05
forum: Multimedia Software
---

### Post by PeterBrinck on 2012-05-05
Hi.
Im really new to Ubuntu.
And i want to go up in resolution. My graphics crad support 1920*1080 and my screen does to.
But how do i change to 1920*1080?

Currently i have it on 1680*1050, and if i take 1920*1200 its gets too large!

So how do i change it to be exactly 1920*1080?

Hope someone can help me! Thanks

---

### Post by shantiq on 2012-05-06
hi Peter

install    ```
 sudo apt-get install nvidia-settings
```

pick display configuration

choose  1920x1080


apply/save

[ATTACH]217390[/ATTACH]

---

### Post by jocko on 2012-05-06
> **shantiq said:**
> hi Peter

install    ```
 sudo apt-get install nvidia-settings
```pick display configuration

choose  1920x1080


apply/save

[ATTACH]217390[/ATTACH]
Why do you assume PeterBrinck has an nvidia graphics card? He did not say anything about which graphics card he has...

---

### Post by shantiq on 2012-05-06
absolutely right :KS   i did [and maybe should not presume] but then again he might :KS
so what should he do if he has not?

---

### Post by jocko on 2012-05-06
> **shantiq said:**
> so what should he do if he has not?
Tell us what graphics card he has, and which driver it uses. Without those vital pieces of information no one will be able to help him.

---

### Post by shantiq on 2012-05-06
Peter tells us he is new to Ubuntu so maybe to show him how to do that will be of help


```
lspci | grep VGA
```    i think that is the one


and if you have Nvidia see above:KS

---

### Post by PeterBrinck on 2012-05-06
I have AMD Radeon HD 6500M/5600/5700 Series :)

But how do i install the code thingy?

---

