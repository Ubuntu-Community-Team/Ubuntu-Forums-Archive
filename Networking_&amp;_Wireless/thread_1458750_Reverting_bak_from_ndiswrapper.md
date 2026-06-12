---
title: "Reverting bak from ndiswrapper"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by Rustybolts on 2010-04-20
Using karmic on acer aspire 5332.
Wifi was working from fresh install but would drop out often and sometimes freeze laptop resulting in hard reset.
Installed Ndiswrapper to try windows wireless drivers unfortunately i can't get them to work. How can i revert back to original supplied drivers?

---

### Post by Crafty Kisses on 2010-04-20
Remove the driver by running the following:
```
ndiswrapper -e (drivername)
```

---

### Post by Rustybolts on 2010-04-20
Ty for reply but have already have done complete reinstall of ubuntu. Luckily or unluckily had not much installed as i bodged it up day before trying to get graphics card to perform better (bad drivers intel gma4500m). 
:popcorn:

---

