---
title: "Huge memory leak in indicator-datetime-service"
date: 2011-02-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jmmL on 2011-02-09
After about 60 minutes of uptime indicator-datetime-service is at about 700MB and 94% CPU usage. After ending it, it restarts with the same high CPU usage, leaking about 2MB per second. Killing or ending just respawn it. I've stopped it for now.

Anyone else seeing this behaviour?

---

### Post by dino99 on 2011-02-09
i386 here

dont have issue. maybe related to bug 714763

you might reconfigure it or remove/purge then reinstall it

[https://bugs.launchpad.net/indicator-datetime](https://bugs.launchpad.net/indicator-datetime)

---

### Post by MacUntu on 2011-02-09
Check to see if there's anything geoclue-related in the logs.

---

### Post by jmmL on 2011-02-09
I'm seeing messages like this in kern.log ```
indicator-datet[1689]: segfault at 0 ip 00007fa924ee7b35 sp 00007fff983a5ed0 error 4 in libgeoclue.so.0.0.0[7fa924edd000+14000]
```

I've purged and reinstalled it, and then killed it (haven't rebooted yet). Still the same problem.

---

### Post by dino99 on 2011-02-09
> **jmmL said:**
> I'm seeing messages like this in kern.log ```
indicator-datet[1689]: segfault at 0 ip 00007fa924ee7b35 sp 00007fff983a5ed0 error 4 in libgeoclue.so.0.0.0[7fa924edd000+14000]
```

I've purged and reinstalled it, and then killed it (haven't rebooted yet). Still the same problem.

wrong order :(

kill it first

---

### Post by MacUntu on 2011-02-09
[nothing to see here]

---

### Post by scradock on 2011-02-09
> **jmmL said:**
> After about 60 minutes of uptime indicator-datetime-service is at about 700MB and 94% CPU usage. After ending it, it restarts with the same high CPU usage, leaking about 2MB per second. Killing or ending just respawn it. I've stopped it for now.

Anyone else seeing this behaviour?

What is this indicator-datetime-service you are speaking of?

Here the program fails to start because it cannot find a geoclue provider, or some such nonsense. As far as I can see, the use of geoclue is to try to verify the Timezone, which is information already known to the system. Can there not be a fallback to known data if geoclue cannot connect?

---

### Post by dino99 on 2011-02-09
> **MacUntu said:**
> [https://bugs.launchpad.net/indicator-datetime/+bug/714763](https://bugs.launchpad.net/indicator-datetime/+bug/714763)

no need to repeat post #2 :(

---

### Post by MacUntu on 2011-02-09
oops

---

### Post by dino99 on 2011-02-09
> **MacUntu said:**
> oops

no worry, you only have lost 10 points :(

---

### Post by jmmL on 2011-02-09
> **dino99 said:**
> wrong order :(

kill it first

Maybe I'm being a bit slow today, but I don't see how I can do that. The instant I kill the process, it respawns. So I'll always be re-installing with the process running (or stopped); I don't see a way to reinstall with the process not running at all.

---

### Post by colorprint on 2011-02-09
I have the same problem :(
high cpu load and memory leak for indicator-datetime-service

---

