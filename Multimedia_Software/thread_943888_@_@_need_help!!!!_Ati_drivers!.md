---
title: "@_@ need help!!!! Ati drivers!"
date: 2008-10-10
forum: Multimedia Software
---

### Post by Twohanzos on 2008-10-10
I know that there are many posts about the ATI drivers not really working well on ubuntu or other linux versions. But I've seen many threads where people were saying that their ati drivers work now. Please if anyone could tell me how to reach this, I dont understand the computer stuff these people talk about, and really would like my graphics card to work. 
Thanks.

---

### Post by markbuntu on 2008-10-11
First, we need to know what you have. There are different solutions depending on the card.

---

### Post by madmetal on 2008-10-11
> **markbuntu said:**
> First, we need to know what you have. There are different solutions depending on the card.

indeed..
open a terminal (Applications >> Accessories >> Terminal) and type
lspci

---

### Post by rudeboy1 on 2008-10-11
I just got ubuntu 8.04 and i have a asus ATI Radeon 9600xt and i see in the xorg drivers it is listed. When i use it and ubuntu loads just before the log in screen i get a error that it doesn't recognize my hardware and asks if i want it load it in low graphics mode.

---

### Post by BMWDriver on 2008-10-11
Go to the [Unofficial ATI Drivers Wiki]("http://wiki.cchmtl.com").
You will find everything related to installation and troubleshooting.

I will add that you should run this command AFTERWARDS to enable video acceleration (video upscaling, optimal DVD playback, etc.) for best 2D performance : 

sudo aticonfig --overlay-type=Xv

This site has been the definite cure for me, installing the 8.9 Catalyst drivers from ATI in manual mode.

---

### Post by linux_lover69 on 2008-10-11
> I just got ubuntu 8.04 and i have a asus ATI Radeon 9600xt and i see in the xorg drivers it is listed. When i use it and ubuntu loads just before the log in screen i get a error that it doesn't recognize my hardware and asks if i want it load it in low graphics mode.
Oh this happened to me. I cant remember the options it gave tho. All I remember is once you click one option there is a way to select what graphics card you have then click ok. But for some reason when I did it it didn't automatically restart the computer you to to manually restart it. Sorry its not much help but I cant remember the options.

---

### Post by rudeboy1 on 2008-10-11
yeah i entered the configure option when it is telling me its booting in low graphics mode and picked my moniter and graphics card but i need to save those settings and i dont know where it will let me save them to

---

### Post by linux_lover69 on 2008-10-11
Doesn't It do that already?

---

### Post by rudeboy1 on 2008-10-11
No it asks for a location. If I dont specifie a location when I hit ok and it restarts I still have the same issue and need to redo the config again.

Also when ubuntu starts windows close on there own and when i try to start synaptic or device drivers or a couple others it pops up an error saying

 you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report 

and im to much of a noob to know what to do.

---

