---
title: "Democracy player wont install in Edgy"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by creigscofield on 2007-01-12
When I try to install democracy player the package installer tells me that a dependency cannot be satisfied for mozilla-dev.  So I tried to install mozilla-dev, and I got this;
```
creig@creig-laptop:~$ sudo apt-get install mozilla-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnspr-dev
E: Package mozilla-dev has no installation candidate

```
There is no mozilla-dev in synaptic and I am completely lost.  Any help would be greatly appreciated. 
](*,)

---

### Post by deadgobby on 2007-01-12
I got DM working when I install Automatix. 
[http://www.getautomatix.com/](http://www.getautomatix.com/)
 Please read how to install it and you'll be haven fun with DM.
Gobby
PS use this command
sudo aptituse install mozilla-dev
 Aptitude has some super cow powers and can solve some of the depends

---

### Post by sloggerkhan on 2007-01-12
I have democracy working without automatix, no problems. I don't remember doing anything special, tho.

---

### Post by creigscofield on 2007-01-12
> **deadgobby said:**
> I got DM working when I install Automatix. 
[http://www.getautomatix.com/](http://www.getautomatix.com/)
 Please read how to install it and you'll be haven fun with DM.
Gobby
PS use this command
sudo aptituse install mozilla-dev
 Aptitude has some super cow powers and can solve some of the depends

All hail the super cow powers of the mighty aptitude!  Democracy is up running, thanx!!!

---

