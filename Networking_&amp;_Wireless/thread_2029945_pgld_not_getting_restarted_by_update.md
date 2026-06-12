---
title: "pgld not getting restarted by update"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by Cadmus on 2012-07-20
Hello there, I have pgl installed on my little Ubuntu server, but I've noticed something odd.

I have it set up so my blocklists are updated daily, this works correctly, but pgld isn't restarted and it gets kicked back into life by the watchdog at some point in the 5 mins afterwards.

Is this normal behaviour? Or do I have something not set up quite right?

---

### Post by Cadmus on 2012-07-20
I've added a line at line 72

```
pglcmd restart &> /dev/null
```

That should keep it quiet for now

---

### Post by jre on 2012-07-28
The "update" includes a "reload" which applies the new blocklist to the running pgld process without touching the iptables setup. Contrary a "restart" stops pgld, removes the iptables, sleeps one second, adds the iptables and then starts the pgld process. So you have a short time unprotected. Therefore reload is better then restart.


We should find the reason why pgl crashes frequently for you, which then triggers the watchdog-restart at some time.
Which version do you use? Do a "dpkg -l pgld". You definitely need to update to 2.2.1 which fixed a related bug.
If this doesn't help:
What was the actual watchdog message (that is in the pglcmd.log and sent to you/root per mail). Are there any other hints in the pglcmd and pgld logfiles?

Of course until we find the solution, your workaround is better then doing nothing at all. Please note that every update will remove your workaround, so you need to reapply it afterwards again if you eperience problems.

---

