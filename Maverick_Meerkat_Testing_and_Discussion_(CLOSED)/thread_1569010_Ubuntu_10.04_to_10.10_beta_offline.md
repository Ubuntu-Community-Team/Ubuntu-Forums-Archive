---
title: "Ubuntu 10.04 to 10.10 beta offline"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by meadhikari on 2010-09-06
I just downloaded the beta from the Ubuntu site.
Now can I update my system offline?
No internet connection in my machine.

---

### Post by nacho32 on 2010-09-06
you really should have a internet connection. catch22

---

### Post by uRock on 2010-09-06
If you are not sure of how to run an upgrade, then running a testing version may not be beneficial. 10.10 has almost two months to go before it will be released to the world.

---

### Post by ronacc on 2010-09-06
without an internet connection do not install/upgrde to the beta , many updates come out every day and without a network connections you would not get them .

---

### Post by PaulW2U on 2010-09-06
> **ronacc said:**
> without an internet connection do not install/upgrde to the beta , many updates come out every day and without a network connections you would not get them .
Exactly, the other day I received 129 updates, today 43 (so far).

---

### Post by 67GTA on 2010-09-06
You can download the 10.10 alternate daily CD iso, and update from it. Just add it as a CD repo. It will contain all updates that are put in daily. You might have a few niggles out of graphics drivers, etc.

---

### Post by thatguruguy on 2010-09-06
> **uRock said:**
> If you are not sure of how to run an upgrade, then running a testing version may not be beneficial. 10.10 has almost two months to go before it will be released to the world.

Actually, one month and four days.  But, who's counting?

---

### Post by meadhikari on 2010-09-07
Can I conclude that I should not and can not do that.

---

### Post by howefield on 2010-09-07
> **meadhikari said:**
> Can I conclude that I should not and can not do that.

If you have no way of getting the new packages, then you cannot update your system. If you can get the packages... then you can.

A whole lot of hassle to keep it updated regularly without an internet connection. ;-(

There may be a Loco team close by that might be able to offer a solution ?

[https://wiki.ubuntu.com/LoCoTeams](https://wiki.ubuntu.com/LoCoTeams)

---

### Post by jerrylamos on 2010-09-07
> **meadhikari said:**
> Can I conclude that I should not and can not do that.

Meadhikari,

I'm used to running early Alpha, Beta, ... which I load into a separate partition, looking for bugs to report.  For me with my hardware Beta did run without updates.

I'm not sure what your objective is in running early unstable version, but if it is in a separate partition you can boot it, try it, then boot your previous one when you want.

Updating from a CD is supposed to work.  In Synaptic you flag the CD as a source of updates.  CD live wasn't updated until today see:
 [http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

I use rsync which updates changes from the .iso I have already and the .iso in daily build.  Faster and cuts down internet traffic.

Do note that certainly during Alpha and even Beta an update can cause bugs and failures of X or booting or whatever so I always have a test partition for that.

Jerry

---

