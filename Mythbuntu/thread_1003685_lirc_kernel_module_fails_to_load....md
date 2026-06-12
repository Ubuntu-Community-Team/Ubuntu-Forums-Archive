---
title: "lirc kernel module fails to load..."
date: 2008-12-06
forum: Mythbuntu
---

### Post by hardyn on 2008-12-06
watching the verbose boot, the final kernel module, lirc, returns failed when attempting to load at boot; but the remote does work and lirc does seem to accepting data.

why am i getting this returned failed state, failed does not seem like a good thing to me?

thanks in advance for any help.

---

### Post by hardyn on 2008-12-06
forgot to add that the mythbuntu version is 804... i did initially try 810 but it won't stay running; crashes all over its self.  no kernel panic, just hangs all over the place, sometimes will run for a hour or so, sometimes 30 seconds; 804 runs fairly well, so i would like to think its not hardware related.

i don't remember having this failed message with 810, but it will not stay running so it does not help me.

---

### Post by majoridiot on 2008-12-07
> **hardyn said:**
> watching the verbose boot, the final kernel module, lirc, returns failed when attempting to load at boot; but the remote does work and lirc does seem to accepting data.

why am i getting this returned failed state, failed does not seem like a good thing to me?


if your remote works, it doesn't seem like anything to be too concerned about.

once you are booted, log into a terminal and restart lirc by hand:
```
$ sudo /etc/init.d/lirc restart
```

if it stop and restarts ok and your remote works, no worries. ;)
> **hardyn said:**
> forgot to add that the mythbuntu version is 804... i did initially try 810 but it won't stay running; crashes all over its self.  no kernel panic, just hangs all over the place, sometimes will run for a hour or so, sometimes 30 seconds; 804 runs fairly well, so i would like to think its not hardware related.

i don't remember having this failed message with 810, but it will not stay running so it does not help me.

8.10 was less than stable on two different boxes for me too... with no obvious messages in any
logs that might point out the random freezes.  dunno about you, but my freezes were total- no ssh login
or anything else beyond a hard reset would fix it.

8.04.1 is more than stable.  sticking with that for now.

---

### Post by hardyn on 2008-12-07
i have tried that, the lirc restart.

and it actually fails in the attempt to shutdown and restart the lirc module.  i am not in front of that box right now for the exact message.

but it does work, so i may not worry about it, i just don't like error messages.

---

