---
title: "new glx drivers"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by loserboy on 2006-07-11
do I need to do anything to setup the new glx drivers that was in updates today?

---

### Post by tseliot on 2006-07-11
> **loserboy said:**
> do I need to do anything to setup the new glx drivers that was in updates today?

See the version of your kernel:
```
uname -r
```

you will get something like:
```
2.6.15-26-[COLOR="Red"]k7[/COLOR]
```

The part I put in red stands for the architecture your kernel is optimised for.


Then make sure the restricted modules for k7 are installed (install this dummy package so as to be sure):

```
sudo apt-get install linux-386 (or 686 or k7,etc. according to your architecture)
```

Then you can update whatever you want (and you won't need to repeat this procedure next time there is an upgrade)

---

### Post by loserboy on 2006-07-11
k ill try it when i get home from work thanks

---

