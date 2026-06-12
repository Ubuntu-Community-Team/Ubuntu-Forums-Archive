---
title: "totem hangs the whole system"
date: 2008-07-30
forum: Multimedia Software
---

### Post by voytec on 2008-07-30
When I try to watch a video or a file from youtube it hangs the whole system completely! Nothing works! Neither one off alt + f1 etc. nor alt+ctrl+backspace nor even alt+ prt sc + R E I S U B.
Thanks for your help in advance!

---

### Post by ajgreeny on 2008-07-30
Alt+PrtScr+RSEIUB is what may work, not your version, or perhaps that was a simple typo.  Anyway, it seems likely that your problem is related to either flash not being installed, or not properly at any rate.  Try ```
sudo apt-get install flsahplayer-nonfree
```.  What type of videos other than youtube are you having problems with?

---

### Post by voytec on 2008-07-30
> **ajgreeny said:**
> Alt+PrtScr+RSEIUB is what may work, not your version, or perhaps that was a simple typo.  Anyway, it seems likely that your problem is related to either flash not being installed, or not properly at any rate.  Try ```
sudo apt-get install flsahplayer-nonfree
```.  What type of videos other than youtube are you having problems with?

No it was not typo. I found it like that on this forum. Thank you for correcting it maybe next time it will work :)
I tried to play *.avi. The thing is it not always happen to me. I have just tried and everything worked fine. I have a problem mostly with youtube videos! And this:
```
sudo apt-get install flsahplayer-nonfree
```
did not work.

---

### Post by nikgare on 2008-07-30
Try it like this:

sudo apt-get install fl**as**hplayer-nonfree

---

### Post by voytec on 2008-07-30
> **nikgare said:**
> Try it like this:

sudo apt-get install fl**as**hplayer-nonfree


This is what i get:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer-nonfree

```

---

### Post by nikgare on 2008-08-01
You need to enable restricted and/or multiverse repositories in Software Sources

---

### Post by voytec on 2008-08-01
> **nikgare said:**
> You need to enable restricted and/or multiverse repositories in Software Sources

wow :) English please :) I have no idea how to do that.

---

### Post by ajgreeny on 2008-08-01
Go to System>>Adminstration>>Software Sources and make sure the buttons are checked in all but the CDrom and Source Code boxes.  Then click reload next time you open synaptic or just use the terminal and command ```
sudo apt-get update
```

---

