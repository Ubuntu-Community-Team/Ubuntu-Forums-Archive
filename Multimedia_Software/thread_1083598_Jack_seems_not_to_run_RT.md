---
title: "Jack seems not to run RT"
date: 2009-03-01
forum: Multimedia Software
---

### Post by Zannax on 2009-03-01
Hello,
If I launch jack in realtime mode and try to "inspect" its process priority with a shell command I get:
```
stefano@stefano-desktop:~$ chrt -p `pidof jackd`
pid 8751's current scheduling policy: SCHED_OTHER
pid 8751's current scheduling priority: 0

```

Why isn't it "SCHED_FIFO" and priority 70?

The command line of the jack daemon process is:
/usr/bin/jackd -R -P70 -dalsa -dhw;0 -r44

and I think everything is setup correctly...

---

