---
title: "Addobe flash player"
date: 2012-01-30
forum: Multimedia Software
---

### Post by Wildmanron on 2012-01-30
Hello My name is Ron:
  I am runing three systems two with Ubuntu 11.10 & one with 11.4 .

the one with the 11.4 had 11.10 but my wife took it of and went back to 11.4 because it keep crashing the addobe flash player and now it is doing it in 11.4 also she is playing on the face book city ville Indiana Jones games.

The computer has 495.4 mib of memory showing and p 4, 1.8 ghz processor with 30.9 gib of hard drive and it has a nvidia video card not sure witch one so can some one tell me why it keeps crashing the addobe flash player it done it in 11.10 & it dose it in the 11.4 is there something i can do to stop this  I am still new to this Linux stuff i have been real happy with it sure wish i know more about it but that is why i am asking you for help thanks folks.

it also has a problem of being real slow then it speeds back up but most of the time it is slow..

Thanks for your time in advance folks.

Ron

---

### Post by wolfen69 on 2012-01-30
You are using a *very* resource heavy version of ubuntu for an older computer like yours. I highly recommend installing Lubuntu on a machine like that.
Then simply:
```
sudo apt-get install lubuntu-restricted-extras
```

Lubuntu will run much faster than Ubuntu for you.

---

### Post by Wildmanron on 2012-01-30
ok where do i go to find this  Lubuntu iso and thanks for the quick reply

Ron

---

### Post by bcarlowise on 2012-01-31
Here are my recommendations:

1. Be sure the actual nvidia drivers are installed and in use (not the open source ones). That will reduce the overhead on the CPU(s).
2. Use the Adobe version of Flash instead of the open source version. It is more stable in my experience. When I used the various open source versions of flash I always had instability on flash enabled websites.
3. I run 11.10 perfectly fine on a Pentium 4 machine. LUbuntu may run better but I am not convinced that using 11.10 or even 11.4 is the problem to your flash instability issues. Personally, I find 11.10 to be far more stable than 11.04 so I would recommend either going back to 11.10 or trying LUbuntu.

---

