---
title: "Can't access windows shares on Natty with Nautilus"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by QwUo173Hy on 2011-09-19
I have a sharing dock that I got from Vodafone with our wireless / mobile broadband. I've put some mp3s / movies on it and the windows computers in the house can see them, but not Nautilus.

Nautilus can see the Vodafone network share, but can't take me any further (double clicking does nothing).

 I've tried pyNeighborhood too but that didn't work either. Again, it saw the share but the mouse changed into a timer and stayed there when I tried to mount the share or the folder.

I need a gui solution ultimately so everyone can use it. Any ideas on how to get this working? Does samba not work properly on Natty?

Many thanks,
Jarlath

---

### Post by mlentink on 2011-09-19
Have you checked to see if winbind is installed correctly?

---

### Post by QwUo173Hy on 2011-09-19
> **mlentink said:**
> Have you checked to see if winbind is installed correctly?

Thanks mlentink, I've just checked now and yes, it is installed. Synaptic also has a windbind4 available from an svn source but I haven't installed it.

---

