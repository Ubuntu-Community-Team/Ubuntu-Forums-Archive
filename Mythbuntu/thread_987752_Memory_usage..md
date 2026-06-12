---
title: "Memory usage."
date: 2008-11-19
forum: Mythbuntu
---

### Post by jmail524 on 2008-11-19
Just a quick question.

I have just built a MythTV backend server.  It has an AMD Athlon X2 5600+ processor, 2.0 GB RAM, (3x) 1 TB hard drives (Hardware RAID5), 3 ATSC/HD tuners, and running Mythbuntu 8.10.

Everything seems to be running perfectly.  However, when I go into the "Information" menu and check on the machine status it says that it is using all the RAM in the machine (2.0GB total, 2.0GB used, 20 MB free, 60MB swap used.)

Does this sound normal or should I increase the amount of memory.  (Just trying to head off any future problems.) It streams to 3 frontends. (1x HD, 2x SD)

Thanks.
Brian

---

### Post by Cracauer on 2008-11-19
Linux always uses all RAM.

Programs like that shouldn't report "free RAM". That's a nonsense number of no practical value.

---

### Post by ian dobson on 2008-11-19
Hi,

Don't worry about is, I imagine your apps are using about 400Mb ram and the rest is eing used as cache. If a program requests extra memory the kernel will just stop using some of the cache and give it to the program.

Have a look here for the memory usage on my Quad,4Gb ram, RAID 5, 4 tuner backend:- [http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-memory.html](http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-memory.html)

Regards
Ian Dobson

---

### Post by jmail524 on 2008-11-21
Thanks for the replies.

I wasn't too worried about the memory usage because everything seemed to be working properly.  I just wanted to make sure it wasn't a problem.  Thanks for the confirmation.

Brian.

---

