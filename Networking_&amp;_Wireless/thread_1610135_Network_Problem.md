---
title: "Network Problem"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by .Impact. on 2010-10-31
This is my first time to use Linux.
I installed Ubuntu via Wubi (in windows os)
and i have that damned wireless card AirForce One (Broadcom -.-')
but i managed to install driver using this method
downloaded ```
broadcom-wl-4.150.10.5.tar.bz2
```
installed ```
b43-fwcutter
``` from Ubuntu cd
and I moved 
```
wl_apsta_mimo.o to /lib/firmware 
```
and wireless stations appeared.
Than i opened terminal 
typed 
```
pppoeconf
```

And set that up.I connected to internet and Ubuntu downloaded 80Mb of updates.
PC restarted and this happened:
[IMG]http://img808.imageshack.us/img808/3936/wardl.jpg[/IMG]

Now,i dont have internet at all (like its disabled) 
when i type ```
pppoeconf 
``` in console 
it says something like "sorry i scanned two interfaces but..."
SO i dont have internet and dont know what to do now :S

Heeeelp please

:popcorn:

---

### Post by .Impact. on 2010-10-31
BUMP!!!
Help please,anyone?

---

### Post by Iowan on 2010-10-31
Bumping no more than once/day is generally considered "polite" - less than an hour is a bit impatient. 

Dunno why Network Manager icon  disappeared - sometimes if it has nothing to manage... You can try adding a "Notification area" back to the desktop. [Here]("http://ubuntuforums.org/showthread.php?t=1505217") is another thread that might be of use.  There are a couple more things to try if one of these doesn't work

---

