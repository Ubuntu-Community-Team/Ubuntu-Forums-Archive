---
title: "LIRC sends double signals"
date: 2016-09-07
forum: Multimedia Software
---

### Post by SagaciousKJB on 2016-09-07
This has been a problem for a while now and it's getting quite irritating and I want to find a better solution.

For some reason, when I press a button on my remote, LIRC doubles the action of the button.  So for example if I press the channel up button, it will go up 2 channels instead of 1.

I found a quick solution doing this 
```
echo lirc > /sys/class/rc/rc0/protocols
```

But it was suggested I put it into /etc/rc.local to make it run on startup...  But it doesn't seem like /etc/rc.local is even executing. I have to manually execute it after logging in.

From what I understand it's something to do with loading two modules for the same remote, but I don't really know what to do about it and I can't find the original site where I found that information.

---

### Post by SagaciousKJB on 2016-09-09
Nobody has any idea?

---

