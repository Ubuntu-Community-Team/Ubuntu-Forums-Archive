---
title: "network yes... internet no"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by rektruax on 2009-12-25
Here's one not quite like the others...

After installing and enjoying 8.10 for the last 2 months now, my Thunderbird, Firefox, Synaptic, etc, won't connect to the WWW. My wireless WMP54G connects to my Linksys router just fine, but won't complete the process of internet. Now here's where my situation seems different...

I'm writing from the same system via an 8.10 live disc right now. It connects. But the installed version won't. I use MAC and not a WEP password.

Any suggestions? Thanks in advance...

---

### Post by Iowan on 2009-12-25
Try to **ping** internet by IP address (209.85.225.103). If that works, check */etc/resolv.conf*. If the machine connects to network, but not internet - it may be DNS problem.

Ordinarily, the DHCP server provides the client with a list of nameservers. If this quit working, there is a way to "inject" your choice of nameservers via the "prepend" line in */etc/dhcp3/dhclient.conf*.

---

### Post by zaphod777 on 2009-12-25
check your dns settings.

---

### Post by falconindy on 2009-12-25
Could also be a missing gateway.

> **rektruax said:**
> I use MAC and not a WEP password.
wat.

---

### Post by ant2ne on 2009-12-25
> for the last 2 months nowWhat changed?

---

