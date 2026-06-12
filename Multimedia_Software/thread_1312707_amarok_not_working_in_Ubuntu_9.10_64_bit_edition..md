---
title: "amarok not working in Ubuntu 9.10 64 bit edition."
date: 2009-11-03
forum: Multimedia Software
---

### Post by dineshbabumm on 2009-11-03
Hi friends,

I recently installed Ubuntu on my newly purchased Dell vostro 1520 laptop. Since it is a 64bit machine (Intel core2duo T6670) I installed 64 bit edition of Ubuntu. I installed amarok which got installed without any error. But when I try to play songs, it is not playing. Infact when I select songs, nothing is getting selected. I even tried opening song through amarok unsuccessfully.

This problem was there in Ubuntu 9.04 and I hoped it won't be there in Ubuntu 9.10. I recently installed Ubuntu 9.10 and the problem still persists. I have installed Exaile instead and it is working fine. All other players including VLC, Movie Player, Real player are working and so I guess codecs aren't any problem in this case. Is this a problem with 64 bit version of amarok?

I installed it through the repositories by the by. Typed sudo apt-get install amarok and it got installed. If any one has any solution please share it. 

Thank you very much,
Dinesh

---

### Post by dineshbabumm on 2009-11-03
Bounce. Please help.

Thanks in advance,
Dinesh

---

### Post by dineshbabumm on 2009-11-03
okay found the solution.

This one works:
sudo apt-get install libxine1-plugins

Seems many had the same problem and found the above solution from another thread in x86_64 bit forum here. :-)

---

### Post by parthpatil on 2009-11-04
Thanks a lot , that fixed it!

---

### Post by ZaHACKieL on 2009-11-10
Thank you very much. This solved my problem too. If you can, tag it as [SOLVED].

Thanx!

---

### Post by BFG on 2009-11-11
I had the same, Amarok would create a playlist but wouldn't attempt to play them.  
Amarok --debug showed error:
**Cannot find demultiplexer plugin for MRL**


> **dineshbabumm said:**
> sudo apt-get install libxine1-plugins

Perfect!!  Solved it.   Many thanks dineshbabumm.

---

### Post by CaptMorgane on 2010-06-10
You saved another ubuntu noob!  

Thanks!

---

### Post by pdemutti on 2010-06-17
This solved my problem !
it worked in my HP pavilion dv5-1240br perfectly
thanks a lot!

---

