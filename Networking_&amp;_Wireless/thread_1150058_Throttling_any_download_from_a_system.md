---
title: "Throttling any download from a system"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by kspn on 2009-05-05
Hi,

I need to throttle the bandwidth used by a (x)Ubuntu system for system updates (as well as updated Linux Install Images ect) I have found a solution _[here]("https://www.linuxquestions.org/questions/linux-networking-3/traffic-shaping-with-iptables-353672/")_ which might do the trick, with appropriate modifications.

I was wondering if anyone had any other options that might work.

I would be creating a couple of scripts, one to limit the speed during Peak Download time and another for Off-Peak, then activating the scripts using CronTab.

I need to limit the bandwidth used by **any** download on the system that is not LAN (so that I can still copy files via the Local LAN), whether it is an image update, system update, firefox download, YouTube, ect.

Thanks in Advance.

---

