---
title: "fglrx lockup on shutdown"
date: 2011-04-04
forum: Multimedia Software
---

### Post by naasking on 2011-04-04
I'm not 100% certain, but I'm fairly sure that fglrx is preventing clean shut downs. Hardware is an ASUS E-35M1-I Deluxe, so fairly new, and I'm running Ubuntu natty.

I couldn't find anything wrong in the logs under /var/log, so I'm not sure where I can look to find the specific errors. All I know is that when I'm running with fglrx shutdown takes forever, as if it's waiting for the X server, and it just never shuts down cleanly, forcing a disk check on the next boot. When I run with the standard radeon driver everything shuts down quickly and cleanly, so it's not a hardware problem per se.

When I tried to execute a "service slim stop" or "service gdm stop" while running fglrx, the whole system would often hang, needing a hard reset.

Any suggestions?

---

