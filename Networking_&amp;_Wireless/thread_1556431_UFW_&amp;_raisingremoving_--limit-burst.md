---
title: "UFW &amp; raising/removing --limit-burst"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by Nextraztus on 2010-08-19
Hello- 

I have recently deployed our new webserver and now that the "real world" is hitting it, I'm doing the  "watch syslog and cleaning up problems I didn't see during internal testing" thing.

Something I've noticed is a lot of log messages for limit-burst violations. Our server is behind a firewall upstream that handles DoS attacks, so I want to go ahead and remove the limit bursting protection. I did research some of the "offending" IP addresses and I'm pretty sure they are legit connections getting blocked.

What is the proper "UFW-Way" of doing this so that the settings stick at reboot?

I looked in /etc/ufw/before.rules and I see the line that says something like:
```
"-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny"
```

Do I just remove the -m limit --limit 3/min --limit-burst 10 portion? Or is there a better UFW command for it?

Thanks in advance!

---

