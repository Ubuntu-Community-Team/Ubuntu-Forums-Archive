---
title: "UFW stop logging for a specific port"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by gohsthb on 2009-11-18
I keep getting lines in my log files like below:

```
Nov 18 11:42:19 CEC-Shop kernel: [18599.627678] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:8c:7d:07:95:08:00 SRC=10.10.10.80 DST=255.255.255.255 LEN=239 TOS=0x00 PREC=0x00 TTL=64 ID=32308 PROTO=UDP SPT=10260 DPT=10260 LEN=219
```

I know this is a print server on my network.  I simply want my firewall to not log the rejected packets on port 10260.  I tried adding the following line in /etc/ufw/after.rules, but it did not stop logging for that port.

```
-A ufw-after-input -p udp --dport 10260 -j RETURN
```

The section that line falls under is commented "don't log noisy services by default" so I figured that adding 10260 to the list would stop logging it.  Anyone have any ideas?  Thanks.

---

### Post by spezticle on 2012-02-26
bump!
i'm working on this task as well, though with a different scenario in the logfile entry. yours is a broadcast, whereas i'm just trying to filter noisy services, torrent connections

OP it's been a few years but hopefully you've solved your problem and have some insight?

---

### Post by overdrank on 2012-02-26
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

