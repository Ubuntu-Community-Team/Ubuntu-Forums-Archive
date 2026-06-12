---
title: "Noob. nVIDA Video working or not?"
date: 2010-10-01
forum: Multimedia Software
---

### Post by mrchaos101 on 2010-10-01
Hello. I killed windows and jumped to Ubuntu after thinking about it.
I know windows systems very well and been on the PC starting in the DOS age.

First off. I think I have everything going. I had issues with the display and sound. I got the sound working thanks to these forums...but I have "tossed" some code in the command window that I have no clue what it does or if it worked.

I would like to know if my nVIDIA cards are working correctly. My goal is to use WINE or Play On Linux and get World of Warcraft up and going... along with MS OFFICE 2010.

Im still learning the system and where what is so please go slow.  What Do I need to do to get system information for help? ANd to check to make sure drivers are loaded and working?

i7 CPU
12 GIG DDR3 PC 15,0000
3 Raptor Drives 10kRPM in Raid 0
1 250 GIG 7200RPM storage drive
2 nVIDIA 285's in SLI
1600W PSU


Thanks

Chaos.

---

### Post by NT4usB on 2010-10-03
```
cat /var/log/Xorg.0.log | less
```and arrow or PgDn and look for things nvidia.
or
```
cat /var/log/Xorg.0.log | grep -i nvidia | less
```
will find nvidia.

Also look for (WW) or (EE) for bent or broken stuff.

---

