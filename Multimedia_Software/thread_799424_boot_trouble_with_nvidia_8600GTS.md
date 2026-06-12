---
title: "boot trouble with nvidia 8600GTS"
date: 2008-05-19
forum: Multimedia Software
---

### Post by nitsthegame on 2008-05-19
guys i recently updated from 7.10 to 8.04 and installed the restricted driver for NVIDIA 8600GTS but now i am unable to boot LINUX using my graphic card.

Once ubuntu is over showing the progress bar instead of going to the welcome screen it goes over to a dos window and shows that it has failed to load swap.

My system config are as follow:-

Intel core 2 duo 1.86
Intel 965RY motherboard
300+80 GB sata hdd
1 GB DDR2 Ram

the system is dual boot with win xp and linux ubuntu 

linux still boots with onboard graphics.

---

### Post by Deeta on 2008-05-19
One thing that might help people to ascertain what exact trouble ails you would be if you could issue a 'dmesg' command in the console (the thing that looks like the DOSbox in Ubuntu :)

dmesg is short for diagnostic messages and will replay info gained during boot.

you could also do a 'dmesg > boot_messages' in order to have the messages saved into a file named 'boot_messages' (easier to handle mayhap)

anyways, the more specific the error message the more likely one of us can help ^-^

---

### Post by nitsthegame on 2008-05-20
sorry but i am a total newbie to linux

but i dont know how to work the command u told me

it is a segmentation fault 
thats wht it says after that i cant work any command so i dont know   
how to work the command u told me

pla help me out

---

### Post by Deeta on 2008-05-20
You said that directly after the boot process stops that you are in a type of 'dosbox'.
There should be a cursor around which allows you to input commands.

Just enter 'dmesg' at this command prompt and press 'enter'

right now we here in the forum do not know exactly why the segmentation fault happend.
You said it might have something to do with the swap drives not being mounted or perhaps with some driver install gone wrong of your NVIDIA GPU.

After we figured out what exactly went wrong it would likely be prudent to post a new thread within the 'absolute beginners' forum with the exact error message so that someone with a similar problem can help. The multimedia and video forums are a bit low-key for a problem of your magnitude :D (which is not being able to boot into some usable system at all :)

P.S.: there is of course always the option to just re-install... quite crude but it might be faster in the end. (given that already a day has passed)

---

### Post by nitsthegame on 2008-05-20
well for your info dmesg doesnt return anything
the cursor moves to the next line with enter press

this info is wht is available above the cursor:

Mounting local file system:
fuse: mount failed: Device or resource busy
init: rc-default main process(5049) killed by SEGV signal

---

### Post by nitsthegame on 2008-05-21
this is the pic if the error screen

---

### Post by Xiong Chiamiov on 2008-05-23
That seems more like a problem with your rc-default file, though it could quite possibly be something else, since the last thing to show up isn't always what's causing the problem.

Are you able to boot into recovery mode?

---

### Post by nitsthegame on 2008-05-23
i am able to boot using my onboard graphic card

---

### Post by Deeta on 2008-05-23
> **nitsthegame said:**
> i am able to boot using my onboard graphic card

Wow :) That is weird. And indeed a good reason why you said that the trouble might be connected to the Nvidia8600GTS

Strange thing is that I have a pretty similar setup.
Asus M2A-VM (with RadeonX1250IGP) and an added Nvidia8600GT in my PCIEx16 slot.

I never encountered a similar problem though :-/

Perhaps someone else here knows why adding a GPU might cause such errors.
(problem is of course that if the trouble is related to an Nvidia binary then there is a big chance that only NVIDIA will be able to help, and the quality of their GNU/Linux drivers is like an afterthought when compared to their effort to cater to the Windows world)

---

