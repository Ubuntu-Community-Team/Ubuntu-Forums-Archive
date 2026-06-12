---
title: "Sound problems on my presario cq61-104EL"
date: 2009-06-11
forum: Multimedia Software
---

### Post by Laya on 2009-06-11
hi, i have installed ubuntu 9.04 but i can't hear any sound from the speakers. The headphones works normally, i was searching on web, but i can't find solution. Please help me, i am desesperated.

Thanks!

---

### Post by Laya on 2009-06-12
Hi! Any idea? Please, i am desesperated... I want to hear sounds from laptop's speakers... Thanks!!

---

### Post by LuFra on 2009-06-13
:cry:
Same problem, I try to do this by the shell:
Update ALSA  using

1) sudo apt-get install build-essential
2) wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)

at this i can't do  

tar xvpjf alsa-driver-1.0.15.tar.bz2-( 


any help?

---

### Post by zibuntu on 2009-07-01
hello, iwe got an cq61-100so, and i had to choose model by modprobing manualy to get internal speakers to work....
"modprobe snd_hda_intel model=hp-hdx"
if you are unsure how to unload the drivers and reload them with
correct settings, there are good howtos on forums,
a bad excuse for me not being able to write up a good one myself iknow...
i also have the latest snapshot build of alsadrivers and libs,
not sure if it works with the stock ubuntu packages...
hope it helps...

---

### Post by raboofje on 2009-07-01
> **zibuntu said:**
> there are good howtos on forums,
a bad excuse for me not being able to write up a good one myself iknow...

Actually, I much prefer referring to the wiki and improving that as needed, instead of repeating the same advice over and over (in slightly different, incompatible, incomplete ways) on forums :).

In this case: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by zibuntu on 2009-07-01
> **raboofje said:**
> Actually, I much prefer referring to the wiki and improving that as needed, instead of repeating the same advice over and over (in slightly different, incompatible, incomplete ways) on forums :).

In this case: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

i agree totaly, sorry for making a mess, just wanted to say it is possible to make it work, as it does for me.

---

### Post by dbyjazz on 2009-10-25
I had the same problem. That is until I downloaded 9.10 now it works!

---

