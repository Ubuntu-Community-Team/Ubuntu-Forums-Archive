---
title: "Clock is Wrong, did I do the right thing?"
date: 2007-11-25
forum: Mythbuntu
---

### Post by ljbeng on 2007-11-25
Sometime when my pvr box power is reset, the clock will be 6 hours off and of course, Survivor doesn't record :(

I do not have internet connected and I do not get any schedules.

In ubuntu environment, I set the clock manually.

The last time my clock jumped back, the time zone was  set to Central.

Today, I reset the clock to correct Central Time zone time and changed my time zone to London.  Hopefully Mythtv will not try to reset my clock now.

Will this work?  Thanks.

---

### Post by odiseo77 on 2007-11-25
I had a similar problem on Debian Lenny and what I did to solve it was:

```
sudo dpkg-reconfigure tzdata
```

On the menu scroll down to 'Etc', press enter and then select 'UCT'; this should synchronize your system's clock to the hardware clock. The only issue I've noticed after that on debian is that my system seems to *believe* it's on the Greenwich Meridian (GMT) while I'm not, but at least I don't have to set the clock every time I bott into debian.

Hope this works.

---

