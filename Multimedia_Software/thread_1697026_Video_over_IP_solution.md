---
title: "Video over IP solution"
date: 2011-02-28
forum: Multimedia Software
---

### Post by FTMatty on 2011-02-28
Chaps/Chapesses,
I'm working on a solution to bring DVB-T2 video back from a number of sites to one central point. 
I am planning to do something like the following:

30 remote sites with a rack mounted micro-ITX PC and a Black Gold BGT3620 DVB-T2 card, connected via a WAN and hopefully running some sort of linux based media software. 
Ideally I would like to be able to web browse into the individual machines on an adhoc basis to check that the output and control the receiver.

The questions I have are as follows

1) What is the best software to use for web based control/viewing?
2) Has anyone used the Black Gold card successfully in a Linux environment?
3) Has anyone tried any other DVB-T2 receivers?

Any help is gratefully received.

Thanks

---

### Post by aeiah on 2011-02-28
you're probably best looking into making them mythtv backends, although i dont know how well mythtv will stream over the internet. are you looking to record or just stream live channels (like a slingbox)?

mythtv is designed as a PVR environment, with backends (that receive, record, encode, distribute etc) and frontends that are plugged into televisions. it may not be exactly what you're looking for and you may find you dont want to use it but since its the most popular, you should check it supports your hardware. if mythtv doesnt, linux as a whole probably doesnt :p

---

