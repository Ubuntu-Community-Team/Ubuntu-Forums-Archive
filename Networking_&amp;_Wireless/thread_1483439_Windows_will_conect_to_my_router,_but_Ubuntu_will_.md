---
title: "Windows will conect to my router, but Ubuntu will not... what am i doing wrong?"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by LocustsOfSteel on 2010-05-14
I have a Dell Dimension 4600, dual boot with Windows XP home SP3, and Ubuntu 9.04.

I have a GigaFast EE420-R ethernet router, windows has always connected to it with no problem, however ubuntu just wont, even after tons of research i still cannot figure out whats going wrong. ( [edit] I am willing to get another router, but i need to know its linux compatible, and i really don't want it to have wifi)

Both operating systems on my computer connect to the modem directly with no problem, but there are 3 computers in my family and 3 users, and i just cannot hog the modem for myself any longer.

I hope to set up the other 2 computers the same way for my family so they can enjoy Linux for safe Internet usage, and so i wont have to waste my time formating and reinstalling there systems anymore to remove all the wonderful spyware malware and viruses that windows seems to so easily attract.

Please, someone advise me, I'm at my whits end, I don't personally know any Linux gurus, and I really need some help here.:confused:

---

### Post by Iowan on 2010-05-14
I presume **ifconfig -a** shows no IP address. You might try (from a terminal) **dhclient eth0** - it will probably receive no offers, but that's a starting place...

---

### Post by pdc on 2010-05-14
...................... sorry; error

---

