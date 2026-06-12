---
title: "Force Specific DNS Resolution"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by coolguy918 on 2011-12-11
Would it be possible to make it so that just a few specific workstations on our organization's network always resolve a specific hostname to a specific IP address, regardless of what our ISP's DNS server tells it?

---

### Post by papibe on 2011-12-11
Rules on how to resolve a names are set in /etc/nsswitch.conf

This a typical entry
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
So first the process check the files, which is basically /etc/hosts

If you edit all workstations so that they have an entry similar to this:
```
74.125.227.81    site_you_want_to_restrict
```
They all will resolve to that address (in this example is a google's).

Hope it helps.
Regards.

---

