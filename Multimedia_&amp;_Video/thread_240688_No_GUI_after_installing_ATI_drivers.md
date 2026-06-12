---
title: "No GUI after installing ATI drivers"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by Clark Nova on 2006-08-21
Over the weekend I installed the release build of Dapper that I received through the post. I installed all of the updates and then installed the ATI drivers, following a guide in a different section on this forum. 

When my machine rebooted I got "frequency out of range" or similar, suggesting that my resolution was set too high for my 15" TFT monitor. I can use the recovery option that I get on boot but I don't know how to change my default resolution using the command line.](*,) 

Any ideas? 

Thanks from a determined noobie.

---

### Post by halfvolle melk on 2006-08-21
Hi Clark,
In recovery mode try this:
```
sudo dpkg-reconfigure xserver-xorg
```
It will walk you through. Don't worry about most of the question as most defaults will work for you (but do read the questions before pressing enter :)).

---

### Post by Clark Nova on 2006-08-21
Thanks so much, all working again now:cool:

---

