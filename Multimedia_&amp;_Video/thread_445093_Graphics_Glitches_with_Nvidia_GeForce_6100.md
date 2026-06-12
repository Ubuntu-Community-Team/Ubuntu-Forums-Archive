---
title: "Graphics Glitches with Nvidia GeForce 6100"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by ajbucci on 2007-05-15
I've installed three different versions of ubuntu (6.1, 7.04 and feisty, i've also installed the 64 bit version of 6.1) and have experienced this problem on all versions-- i have an nvidia geforce 6100 integrated graphics chip and an AMD Athlon64 X2 4200+ and i keep getting these graphics glitches where my screen "blinks." It doesn't blink black, it blinks as if you were to maximize a window and then minimize it within a millisecond of maximizing it...  basically, it looks as if something pops up onto my screen very quickly then disappears just as quickly, all happening within' a millisecond or less. It doesn't really hinder what i'm doing, it's just very annoying and happens only when i'm moving the cursor or doing something.

Please help, or else i'll go insane ;)

By the way, i've also tried installing the nvidia drivers and the problem remains.

Any help would be appreciated, thanks!:)

---

### Post by Ramunas on 2007-05-15
I had the same problem, and I noticed that it was happening every time my CPU changed the clock speed(hence the cool&quiet technology in AMD 64 cpu's), so disabling cool&quiet in bios got rid of the problem.

---

### Post by ajbucci on 2007-05-15
This is my BIOS: Phoenix - Award WorkstationBIOS v6.00PG

I can't find anything related to cool'n'quiet or cpu throttling or any other power saving features in the BIOS. 

Is there any way to disable cool n quiet or to see if my computer is even using it?

---

### Post by ajbucci on 2007-05-20
I hate bumping threads but I still have been unable to fix my problem. Is there anyone who may be able to help me?

---

### Post by ajbucci on 2007-06-04
I suppose this will be the last time I'm going to bump this. The problem is still unresolved.

---

### Post by OlleEriksson on 2007-06-11
Open Synaptic and delete the package "powernowd". It solved the same problem for my friend, who has a Nvidia GeForce 6100 integrated on his motherboard.

Hope it helps.

---

### Post by ajbucci on 2007-06-12
Thank you very much. It solved my problem.

---

### Post by twizzy on 2007-10-15
Hello I have the same problem but where is   Synaptic

---

### Post by twizzy on 2007-10-15
Bump!

---

### Post by ajbucci on 2007-10-15
Synaptic package manager, it's under administration or something like that. (I haven't used gnome in months)

If you look hard enough in the menus on the top of the screen you'll find it. Then just search for the powernowd package and remove it.

---

