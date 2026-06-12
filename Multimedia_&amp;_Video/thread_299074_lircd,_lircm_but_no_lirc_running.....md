---
title: "lircd, lircm but no lirc running...."
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by OldGaf on 2006-11-13
OK..... I have been working on this for some time now. I have myth installed and working just fine. My only problem is I can't get lirc to work.

nial@mythtv:~$ ls -l /dev | grep lirc
srw-rw-rw- 1 root root           0 2006-11-13 16:50 lircd
prw-r--r-- 1 root root           0 2006-11-13 16:50 lircm

I should also have lirc running but do not. My Brother has it working on his system. We both use the same CD's / scrips / repos. Both have the latest Dapper, Mythtv 20 and lirc 8.

The only diff is his mother board has no IR support built in and mine does, and his is a nvidia chip set and mine is SIS.

Does anyone know if there are chip set issues or whether it matters if your MoBo has IR built in?

---

### Post by OldGaf on 2006-11-19
Update....

I put my hard drive into my brothers PC..... lirc works fine. Put drive back in my box...... no lirc!

My board is a Winfast K7S.

Also, my board has IR suport as an option. When I look at my board it does NOT have an IR connector, just a place where one could have been added at the factory. There is IR settings in the BIOS, but I have tried AUTO, ENABLED and DISABLED..... no dice!

Any help would be great....

---

### Post by OldGaf on 2006-11-20
Wow..... thank's for your insite!

---

