---
title: "ATI Radeon x700 acting as nVidia GeForce 9300??"
date: 2009-05-13
forum: Multimedia Software
---

### Post by exProphecy on 2009-05-13
Hey guys, so I am currently using Ubuntu 9.04 and I found out that the ati drivers provided in the Synaptic Package Manager does not work with my ATI Radeon Mobility X700. Even with this problem, I decided to try and play Counter-Strike (the original). Before I ran it, it said my graphics card driver is out of date and I should update it. To my UTMOST surprise, it said my graphics card is an nVidia GeForce 9300. What the heck?! Anyways, it is most certainly NOT an nvidia, as it is an ATI. So I tried playing it and it actually runs. Except, it's running @ low performance. I get 20 FPS on avg and sometimes 12 FPS when there are a number of people on the screen. But usually, on Windows XP, my avg in Counter-Strike: SOURCE is 30 FPS. So I was wondering, what should my next course of action be? I tried to find out what to do on my own and someone said something about installing "open source ati drivers"? How do I do this? Since the proprietory drivers won't work and all..

---

### Post by eldragon on 2009-05-13
its probably running under vesa since your graphics card is not supported by the catalyst 9.4 drivers... and 9.3 will not work under jaunty.

you will need to install and use the open source ati drivers instead.... and live with the performance penalty this brings.....good luck on your next ati purchase ;)

---

### Post by exProphecy on 2009-05-14
Um okay, so as one of my questions was.. how do I install the open source drivers?

---

### Post by exProphecy on 2009-05-14
So.. does anyone know how to enable the open source ati drivers?

---

### Post by Megamanic on 2009-05-14
You could "downgrade" to Ubuntu 8.10 & install the Catalyst 9.3 driver that does support our graphics cards.  Depends on how important the games are to you...

---

### Post by exProphecy on 2009-05-14
Nah, I like 9.04. But anyways, so can anyone tell me how to set up so it uses open source ati drivers?

---

### Post by Skripka on 2009-05-14
> **exProphecy said:**
> Nah, I like 9.04. But anyways, so can anyone tell me how to set up so it uses open source ati drivers?

Go in Synaptic and look for the Radeon driver.

---

### Post by exProphecy on 2009-05-14
Is it the "xserver-xorg-video-radeon" ? I already have it. Is it not enabled? How do I enable it? How come Counter-Strike is still using sucky graphics? Is there a way I can make it see that I have an ATI not an NVIDIA?

---

### Post by Skripka on 2009-05-14
> **exProphecy said:**
> Is it the "xserver-xorg-video-radeon" ? I already have it. Is it not enabled? How do I enable it? How come Counter-Strike is still using sucky graphics? Is there a way I can make it see that I have an ATI not an NVIDIA?

I refer you to this document:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

To make sure you don't have any fglrx driver bits left over.  

The Radeon driver realy only does 2d at this point, with 3d support only on certain cards at this point-it is very much a work in progress...but better than no driver at all.  If your machine is using the Radeon driver, this is probably why you're getting low FPS in games.

---

### Post by exProphecy on 2009-05-14
Oh it says my card has 3D support. Also, how come CS is reading it as an NVIDIA if it's using the Radeon drivers?

Thanks for the link!

---

### Post by Skripka on 2009-05-14
> **exProphecy said:**
> Oh it says my card has 3D support. Also, how come CS is reading it as an NVIDIA if it's using the Radeon drivers?

Thanks for the link!

I honestly don't know why it is reading your chipset as it is.  That is bizzarro-Ubuntu at work.

---

### Post by Megamanic on 2009-05-15
I've seen the same phenomenon with my ATI card being reported as Nvidia on 9.04

---

### Post by exProphecy on 2009-05-15
> **Megamanic said:**
> I've seen the same phenomenon with my ATI card being reported as Nvidia on 9.04

In what program, if you don't mind me asking?

---

