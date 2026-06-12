---
title: "upgrade hardware = headache"
date: 2008-12-03
forum: Mythbuntu
---

### Post by 4dognight on 2008-12-03
So, I was running my MB on a P4 1.6 with an AGP nvidia FX5200. 
The P4 could not play back HD, so I decided to upgrade. I got a AMD 4850 dual core 2.5 and an abit AN-M2HD MB, 2 GB ram. This version of the MB was neutered of its builtin Video. Didnt matter though as I wanted TVout anyway. So , I picked up a PCIe nvidia 6200 TC. 

I did a fresh install of mythbuntu 8.04. All went smooth except for the video. I installed the nvidia driver via the MCC. And now once I fire up anything using Xorg, the machine seems to freeze up. I can ssh in, and notice Xorg is hogging all the CPU.

Googling around reveals, the 'Option "useEvents" "True" fix. I add itto the xorg.conf, reboot and the same crap happens. Xorg gobbles up all CPU, and its a no show. If, I disable the nvidia driver, All seems to work, I can even watch live TV, except I cant get TVout.

So whats up with Xorg ????

BTW. I also created another server for a FE, using the same MB, and CPU, but with a nvidia 6600 GT, and it works perfect.

Any help is appreciated.

---

### Post by jMon54 on 2008-12-04
I have had luck just trying different nVidia drivers.  I suggest you use the program Envy to help with this.  Once you get this working right, I think you will be quite pleased with the results.

---

### Post by 4dognight on 2008-12-04
> **jMon54 said:**
>   I suggest you use the program Envy to help with this.  

After more googling , I saw some posts about envyng, and tried it. I still get the same results.:frown:

---

### Post by newlinux on 2008-12-04
maybe take a look at 

/var/log/Xorg.0.log


to see if it identifies any problems going on with your X. Also just to double check, make sure you put the UseEvents line in the right place in your Xorg.conf (in the nvidia driver Device section)

---

### Post by 4dognight on 2008-12-04
> **newlinux said:**
> maybe take a look at 

/var/log/Xorg.0.log


to see if it identifies any problems going on with your X. Also just to double check, make sure you put the UseEvents line in the right place in your Xorg.conf (in the nvidia driver Device section)

I  looked in the log. It doesnt show any errors. I do see a line indicating it picked up the "useEvents" option. Which I had placed in the Device section.

Is there any pgm that can be used to 'dump' what the nvidia driver has configured?

---

### Post by 4dognight on 2008-12-05
I did another fresh install, to see if it made a diff, but still the same problem. I then swapped it out with the card (6600 gt) from the other server.
I didnt change anything software wise, and the 6600 worked right away. And of course when I put the 6200 in the other machine the problem happens over there now.

So, is there something with these 6200 turbo cache models, that are incompatible with linux? It will not work if I load the nvidia driver. I dont see errors anywhere in the logs, it just makes Xorg go 100% and the system freezes up.

Is it possible its a bad video card? I think it has to do with the turbo cache part of it.

---

### Post by newlinux on 2008-12-05
I know others have used the 6200TC in ubuntu. Maybe a bad card? Maybe a bug in the current drivers and an older driver might work?

---

### Post by 4dognight on 2008-12-05
> **newlinux said:**
> I know others have used the 6200TC in ubuntu. Maybe a bad card? Maybe a bug in the current drivers and an older driver might work?

Perhaps someone here who has a 6200TC working can post which driver version they are running.

Anybody? ):P

---

