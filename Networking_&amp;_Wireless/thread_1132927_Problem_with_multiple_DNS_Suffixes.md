---
title: "Problem with multiple DNS Suffixes"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by vyruz18 on 2009-04-22
Hi,

I'm fairly new to Ubuntu, and am running into a problem which I cannot resolve.
I'm building some virtual servers for my company which will be running Ubuntu server edition (8.04).

The servers are members of an active directory (W2K3 DC) domain.
So far I've got the server set up and working nicely inside the domain.

The problem I have is that our computers are required to have multiple DNS suffixes, 3 to be specific.
And my ubuntu servers , when completely configured through DHCP, will only show 1 server in /etc/resolv.conf, so naturally they are not able to contact a large number of other PC's inside the domain.

I've solved this temporarily by editing /etc/dhcp3/dhclient.conf and using the
```

supersede domain-name "blabla1.domain.com blabla2.domain.com domain.com"

```

But I'd rather have this automated via DHCP.

Any ideas?

Thanks in advance!!

---

