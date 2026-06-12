---
title: "amaroK 2.3.0 and iPod touch 2g"
date: 2010-07-20
forum: Multimedia Software
---

### Post by adamsbryce1495 on 2010-07-20
I have an iPod touch 2g. and amaroK 2.3.0 on ubuntu 10.04. how do i get amarok to see my ipod? im new, and my amarok is empty. i wanna move my ipod music to amaroK, but Amarok doesn't show my ipod. how do i get this to work?

Ideas and suggestions are greatly welcome.
thanks.

---

### Post by Deersindal on 2010-07-29
Having a similar problem...did you ever get it to work?

---

### Post by dotnick on 2010-09-07
I had the same problem.  I noticed that ifuse was not installed by default but after I installed it, it started working.  I tried doing a couple of other steps as well, but I don't know if they were needed.  

There is documentation for an older release that says to create /media/iPod, chmod 777 /media/iPod, the run ifuse /media/iPod.  I also added my user to the fuse group.

Somewhere in there, it all started working.  I even disconnected and reconnected several times.  Hope my stumbling helps.

---

