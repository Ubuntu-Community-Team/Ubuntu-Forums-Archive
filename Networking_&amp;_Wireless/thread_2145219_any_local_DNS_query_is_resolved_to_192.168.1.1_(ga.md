---
title: "any local DNS query is resolved to 192.168.1.1 (gateway)"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by Andre-D on 2013-05-14
This recently started on two 13.04 computers;

 Address:         192.168.1.80
 Prefix:          24 (255.255.255.0)
 Gateway:         192.168.1.1
    DNS:             192.168.1.1

ping hugin   (server)
(results in 192.168.1.1)

ping odin   (server)
(results in 192.168.1.1)

ping randomstring-pwspjws  (non existing name)
(results in 192.168.1.1)

ping vg.no (internet site)
(resolved properly)

Now, the bizzare part: A windows computer on this network (and any virtual windows computer) can still ping hugin, odin, and everything just fine.

So the problem is related to the Ubuntu computers
Also one of the Ubuntu computers logs this in dmesg:

```
[   29.425675] systemd-hostnamed[4017]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Plea
se install nss-myhostname!

```

---

### Post by Andre-D on 2013-05-15
this happens only when my firewall is using OpenDNS

---

### Post by quequotion on 2013-05-15
> **Andre-D said:**
> this happens only when my firewall is using OpenDNS

That sounds a lot like [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1003842").

---

