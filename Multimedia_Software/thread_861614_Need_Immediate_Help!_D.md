---
title: "Need Immediate Help! D:"
date: 2008-07-16
forum: Multimedia Software
---

### Post by !@!@! on 2008-07-16
I accidently messed up my /etc/esound/esd.conf file!
Can someone using Hardy, open a terminal and type
```
sudo gedit /etc/esound/esd.conf
```
and copy and paste what it says in here!
Make sure you've never edited it before, I need a new one!

---

### Post by Cone on 2008-07-17
I'm on Fedora and not Ubuntu, but you could try this one just to see if you want.

```
[esd]
# autospawning is not recommended, since it can't really be done
# right.  If you want your login session to be using a sound daemon,
# you should start it from the session controller, not some random
# app inside.
auto_spawn=0
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

---

### Post by jerome1232 on 2008-07-17
I'm on Ubuntu 8.04 and mine is the same as his so it'll be fine

---

