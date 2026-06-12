---
title: "Change my Motherboard"
date: 2009-05-18
forum: Mythbuntu
---

### Post by liorkr on 2009-05-18
hi i have 8.10 frontend + backend working great
2 days ago my motherboard die and now i can get only newer one
i had gigabyte g945 cheap and now i will get gigabyte g31 
can i replace the mobo without reinstall the whole system ?
I'm kind of new to ubuntu
thanks for help

---

### Post by pawnrocket on 2009-05-18
Yes... 

Not everycase is the same, but I have installed Ubuntu on one system and moved the hard drive to another. The only problem I ever had was with the new intergraded network card. Other then that I was good. All those drivers in the kernel make a big difference. 

But Testing is the key. Like I said not all cases are the same, but I have luck with it.

---

### Post by Dngrsone on 2009-05-18
I concur:  the system should boot up, you may have to do a little configuration work (drivers, etc).

---

### Post by stefangr1 on 2009-05-18
The drivers for all hardware that is supported by default are in the kernel. That means that if your new hardware would work with a fresh install of Ubuntu, it will also work with your old install.

This is not the case when you would have compiled your own kernel. Adapting everything for specific hardware gives a small performance gain, but it results in a loss of generality.

---

### Post by liorkr on 2009-05-18
Thanks for quick help guys 
I'm new to ubuntu so i guess my kernel is not compiled
should i run some command to remove the old drivers?
or its done automatically

---

### Post by Dngrsone on 2009-05-18
It's pretty much plug and play.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/nod.gif[/IMG]

---

### Post by ian dobson on 2009-05-18
Hi,

Swapping the motherboard shouldn't cause too much of a problem.

I've gone from a Intel 965 motherboard to a Nvidia/AMD setup to a Intel Q45 chipset/Q9650 without any problems. I was even able to use the RAID5 array on all the systems without having to install anything.

Before you ask why:- I upgraded from the i965 system to the q45 system and had a spare harddisk that I use in my test/play box which is AMD based.

Regards
Ian Dobson

---

