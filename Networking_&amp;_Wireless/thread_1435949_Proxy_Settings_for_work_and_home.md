---
title: "Proxy Settings for work and home"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by BlazeXI on 2010-03-22
Hi...

i hope someone can help me out here, i recently upgraded to ubuntu 9.10 on my dell d830 ..everything worked great no issues.

did my normal mods and packaged updates and the works.

this laptop i used at work and home, at work i use a windows 7 vm running ontop of my ubuntu and at home well ubuntu of-coarse.

work has a proxy setting and my home network doesnt, so i decided to create two profiles on the system > preferences > network proxy

one for home > with direct Internet connect 
and 
another for work for defined proxy settings

everything was cool...then the one day when i tried to install graphics card driver, it gave a "cant not resolver proxy " error...

i checked my profile and it was on home...i also deleted all profiles and set it to default and it still dont work..

firefox works cause you can set proxy setting directly on firefox , but now i cant do any "apt-get" because some how ubuntu is still picking up my work network proxy setting????

somehow it like stuck on the work network proxy setting although i delete the profiles too...???

could some one please help me out...will be much appreciated #-o

---

### Post by suseendran.rengabashyam on 2010-03-22
Hi,

Did you try clicking on 'Apply System-Wide...' after changing the profile ?

---

### Post by BlazeXI on 2010-03-22
...mmmmm... good point let me try ...

---

### Post by BlazeXI on 2010-03-22
suseendran.rengabashyam you rock buddy...thanks a ton dude..

i apply system wide change,,,and had to reboot for it to take effect...

thank you suseendran.rengabashyam :o

hope you have a super duper day

---

