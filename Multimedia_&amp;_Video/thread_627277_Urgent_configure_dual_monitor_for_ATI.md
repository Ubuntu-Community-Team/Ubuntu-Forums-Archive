---
title: "Urgent: configure dual monitor for ATI"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by seniormartinez on 2007-11-29
Hello, I have read some of the tutorials about ati with dual monitors but none seem to apply to me, everytime i do the commands i get
```

administrador@administrador-laptop:~$ sudo aticonfig --query-monitor
  Connected monitors: none
  Enabled monitors: none
administrador@administrador-laptop:~$ export DISPLAY=:0
administrador@administrador-laptop:~$ sudo aticonfig --query-monitor
  Connected monitors: crt1,lvds
  Enabled monitors: lvds
administrador@administrador-laptop:~

```
and the final command that is supposed to be 
administrador@administrador-laptop:~$ sudo aticonfig --enable-monitor=crt1,lvds
gives me an awful black screen and after a minute it gives me a horrible low resolution but no output whatsoever appears in the monitor.

I will do a presentation about Linux, and i would really love to show it with compiz and all but this just doesn't seem to be working, is there anywhing i can do ?

---

### Post by seniormartinez on 2007-12-01
bump

---

### Post by Mcavity on 2007-12-02
more info would be good. 
what sort of displays are you useing? what ati driver?

---

### Post by seniormartinez on 2007-12-04
i'm using my tv as display connected with a VGA cable and i use the ATI restricted drivers that ubuntu supplies which, correct me if i'm wrong, are the proprietary drivers

---

### Post by bmhm on 2007-12-06
Hi,

_**Situation**_
I am using the Laptop mentioned in my sig, I just switched to gutsy and everything else works fine
I installed the Driver manually, so it's the latest catalyst, AIGLX even works!

**_Symptoms_**
* Still I got 320x200 on both monitors... I wonder why? - using aticonfig --enable-monitors=lvds,crt1 or any other thing like =lvds,none
* When I plug the monitor on gutsy startup, both monitors are correctly enabled, just wrong res & virtual desktop is too big on crt1.

**_Specs:_**
Catalyst: First release named catalyst
ATI X700 Mobility
Gutsy-RT-Kernel (64 bit)

---

