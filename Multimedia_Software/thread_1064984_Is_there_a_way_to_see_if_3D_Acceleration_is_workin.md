---
title: "Is there a way to see if 3D Acceleration is working?"
date: 2009-02-09
forum: Multimedia Software
---

### Post by cforput on 2009-02-09
I have been trying to get my 3D acceleration working for a long time now. My games don't play and I get the dreaded "couldn't find matching glx visual" message. I am going to uninstall the games and reinstall to see if that fixes it. I have done just about every fix I could find related to the error above.

Does anyone know if there is a way to quickly see if 3D acceleration is working? 

I have:
Acer Aspire 5520-5334
NVidia GeForce 7000M
Ubuntu 7.10
Just trying games like SuperTux Kart, nothing real fancy. 
Restricted Drivers has 2 entries:
  Atheros Hardware Access Layer (HAL) - enabled checked and in use
  NVidia accelerated graphics driver (latest cards) - enabled checked and in use

Right now I'm just looking for something simple that I can use to test my 3D. 

Anyone have any ideas for this newbie?

thanks

---

### Post by MarblePanther on 2009-02-09
open up terminal and type:
glxgears

if you dont have it just type:
sudo apt-get install mesa-utils

then run glxgears in terminal

if you see spinning 3d gears, you are accelerated

---

### Post by blufade on 2009-02-13
i just tried " sudo apt-get install mesa-utils"

this is what i get....plz help

> anoop@Anoop-PC:~$ sudo apt-get install mesa-utils
[sudo] password for anoop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 218 not upgraded.

---

### Post by Hellkeepa on 2009-02-13
HELLo!

I quote:
> mesa-utils is already the newest version.
Meaning, it's already installed. Do the first thing **MarblePanther** recommended.

Happy surfin'!

---

