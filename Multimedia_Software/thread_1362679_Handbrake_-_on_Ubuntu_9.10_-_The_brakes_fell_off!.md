---
title: "Handbrake - on Ubuntu 9.10 - The brakes fell off!"
date: 2009-12-23
forum: Multimedia Software
---

### Post by lmbear2000 on 2009-12-23
Just upgraded from Ubuntu 8.10 to 9.10. Tried to update to the latest version of Handbrake (0.9.4) and received and error

Error: Dependency is not satisfiable: libsoup2.4-1 (>= 2.27.92)

I tried removing the previous version and installing again, but no luck.

Any ideas?  I currently can't use the application at all.

---

### Post by JohnAStebbins on 2009-12-23
It sounds like something went sideways with your upgrade.  libsoup2.4-1 is the version that comes with ubuntu 9.10, and it claims it can't find it.

What do you see when you do this:
```

dpkg -l | grep libsoup

```

---

### Post by LuisGMarine on 2009-12-23
I'm surprised your upgrade went fine.  I didn't know you can upgrade straight from 8.10 to 9.10, I was almost sure that you had to go from 8.10 > 9.04 > 9.10.  If not you sure everything is running smooth?

---

### Post by lmbear2000 on 2009-12-23
dpkg -l | grep libsoup

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  grep           2.5.3~dfsg-6ub GNU grep, egrep and fgrep
No packages found matching libsoup.

---

### Post by Hase on 2009-12-26
Same issue.

```
USER@WORKSTATION ~$ dpkg -l | grep libsoup
ii  libsoup-gnome2.4-1                         2.26.0-0ubuntu3                         an HTTP library implementation in C -- Share
ii  libsoup2.4-1                               2.26.0-0ubuntu3                         an HTTP library implementation in C -- Share

```

Aptitude is fully updated/upgraded with all the default apt sources un-commented.

---

