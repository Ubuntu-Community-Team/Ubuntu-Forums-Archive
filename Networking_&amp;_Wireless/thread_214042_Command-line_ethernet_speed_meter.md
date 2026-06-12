---
title: "Command-line ethernet speed meter?"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by tribaal on 2006-07-12
Hi there

I'm trying to mesure transfer speeds for a samba share sitting on a headless server, from the server's point of view (mesure incoming traffic).

How do I retrieve this information from the command line? 

Thanks a lot!

- trib'

---

### Post by mogelhead on 2006-07-12
On my gentoo server i use something like "Internet Bandwidht Monitor" (a command line tool), but I could not find it in ubuntu.

But with ```
apt-cache search bandwidth monitor
``` I found: bmon and bwm, both are commandline.

---

### Post by tribaal on 2006-07-13
Thanks a lot, they both seem to do what I am looking for.

I found something even closer to perfection though, so if anyone cares for a load mesuring utility go for dstat (it has disk io, network io, paging stats, processor usage and much more).

```
sudo apt-get install dstat
```

Cheers :)

- trib'

---

