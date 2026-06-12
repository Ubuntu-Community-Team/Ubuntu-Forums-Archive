---
title: "ATI HD 4500 drivers messed up my ubuntu"
date: 2013-01-27
forum: Multimedia Software
---

### Post by gravitypullsyoudown on 2013-01-27
Hey everyone, I am a ubuntu newbie. I have recently installed 12.10 and tryed upgrading my ATI HD4500 drivers. I think I inserted something like this on the terminal:

sudo apt-get install (...) headers (...) fglrx updates


I had already tried to upgrade the GPU drivers and it messed up my linux. When I rebooted I was presented with "Linux ... incorrect settings... low graphics mode..." something like this. This time, the same thing happened.

So now, I can't even startup in low graphics mode.

Any suggestions? I don't want to re-instal from scratch this thing. But if I do, I'll switch to 12.04.

Thank you!

---

### Post by Bucky Ball on 2013-01-27
*Thread moved to **Multimedia & Video***

Welcome to the forums.

---

### Post by collisionystm on 2013-01-27
Do you get to any kind of a command prompt? 

If so, login at the command prompt and remove the fglrx-updates

sudo apt-get remove fglrx-updates

---

### Post by gravitypullsyoudown on 2013-01-28
Hey thanks for your repply, I'll try to open the terminal with ctrl-alt-T. But I think it will be an unsusseful attempt.

---

### Post by mastablasta on 2013-01-28
> **gravitypullsyoudown said:**
>  I have recently installed 12.10 and tryed upgrading my ATI HD4500 drivers. 
 
 
AMD dropped support from 12.04 onwards for your card. you can use 12.04 or downgrade some elements of 12.10. here is a PPA that will do that: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
 
in this case a better option is to install 12.04 and then add PPA for applications that you need a newer version. as sooner or later you will get into trouble. and besides 12.04 is supported for 5 years, so until 2017
 
another option is to simply use opensource drivers.

---

### Post by Yellow Pasque on 2013-01-28
^Yeah, that. Bug link: [https://bugs.launchpad.net/bugs/1058040](https://bugs.launchpad.net/bugs/1058040)
Ctrl+Alt+F1 might work better for terminal...

---

### Post by Lemuriano on 2013-02-19
A classic example of what happen when one´s depend on proprietary drivers. :( My next laptop will have Intel graphics to avoid the need for this evil drivers. For now I´m lock to use 12.04.

---

