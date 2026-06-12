---
title: "Nvidia Optimus Driver for Linux"
date: 2012-12-05
forum: Multimedia Software
---

### Post by Ventiti on 2012-12-05
Good evening dear all,

I want to install Ubuntu in my laptop. Unfortunately, I heard that ubuntu doesn't support very easily (only over Bumblebee) the optimus technology of nvidia (I have a GT540m). I saw today that there was a recent driver for linux on nvidia's webpage. Does this driver permit to enable the optimus technology so that battery life can be saved?

Thank you all.

---

### Post by goldfish777 on 2012-12-08
Short answer: Yes.

Long Answer:

     So, with bumblebee, you can USE your NVIDIA card. Without bumblebee your NVIDIA card is basically a paperweight. (Unless you can disable the optimus feature on your laptop, in which case you can forget powersaving.) Basically, you install drivers for you integrated card and then you install bumblebee and drivers for the discrete card. After that, you can then run applications on the discrete card using optirun or primusrun. Unless an app is running on the card, bbswitch(tool that comes with Ubuntu's bumblebee package group) will keep the card turned off.  So you get the power saving but it is not dynamic like in Windows. You, the user, get to decide when you want to use the card. The card is turned off only when no apps are running on it. So unless you prefix a command with optirun(e.g. "optirun firefox") your card will never be used.

---

### Post by wormbuntu on 2012-12-09
> **Ventiti said:**
> Good evening dear all,

I want to install Ubuntu in my laptop. Unfortunately, I heard that ubuntu doesn't support very easily (only over Bumblebee) the optimus technology of nvidia (I have a GT540m). I saw today that there was a recent driver for linux on nvidia's webpage. Does this driver permit to enable the optimus technology so that battery life can be saved?

Thank you all.

Goldfish's answer is excellent. I'm using a dell L502 with the same graphics card that you have. I don't game in Ubuntu, so I just appreciate having it turned off - and my laptop runs quieter and cooler than in Windows.

I would just add to be careful on the install as it is possible to screw it up, but there are plenty of threads with good specific instructions on the order in which to install things, and whether to use the nvidea/nouveau driver etc etc.

Good luck.

---

### Post by goldfish777 on 2012-12-09
I am running a Dell XPS L502x with the NVIDIA GT 540M. When you install Ubuntu, sometimes after the install when you check for drivers and such , it may try to install drivers for the NVIDIA card. As long as you don't do that, you will be  OK.

What you want to do is install the bumblebee package from the proper repos.

Check out this wiki page: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Follow those steps after you have booted into your newly installed Ubuntu system and you will be set. 

Despite the fact that the performance of the NVIDIA card under Linux is not quite as good as it is in Window$, it performs pretty well. I find that stuff like Team Fortress 2 in the Steam Beta runs quite well. Also, NVIDIA is working on Optimus drivers for Linux. Pretty soon(hopefully :) ) This laptop will be a nice platform for Linux. I have, at this point, completely ditched Window$. I am running nothing but Linux(A few distros dual booted). 

With Steam coming to Linux, drivers are improving. If fact, NVIDIA claims to have recently doubled performance on there Linux drivers. I think this Optimus issue will soon be over.

There is hope, my friend. :)

---

