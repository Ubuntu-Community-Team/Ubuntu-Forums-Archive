---
title: "BTTV driver needs to be reinstalled every time I reboot"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by fsm on 2007-12-15
Hi,

After several days I have managed to get my Aimslab VHX working with TVTime, but for the following issue:

Every time I boot, it reports No Signal.  The workaround is that I have to:
rmmod bttv
modprobe bttv card=14 tuner=2

After that it works correctly...until the next time I reboot.   Kind of annoying.

Any idea on how I might figure out what is messing up the driver?

---

### Post by Whiffle on 2007-12-15
It probably isn't getting those extra options when you boot, the card and tuner settings.  


I *think* that if you add something like 
```

options bttv card=14 tuner=2

```

to a file in /etc/modprobe.d/  .  You'd do this with
```

gksudo /etc/modprobe.d/options

```

I'm not actually on an ubuntu box right now, so it might not be exact, but I'm pretty sure thats what it needs.

---

### Post by fsm on 2007-12-17
Worked!  Thanks for the help.

Now, if I could only get my card to stay at /dev/video1 (instead of randomly swapping places with my webcam at /dev/video0)

---

