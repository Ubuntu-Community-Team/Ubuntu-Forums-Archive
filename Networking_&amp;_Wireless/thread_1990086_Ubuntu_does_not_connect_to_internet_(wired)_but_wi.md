---
title: "Ubuntu does not connect to internet (wired) but windows does"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by kkostadinov on 2012-05-29
Hi,
I am having issues with connecting to internet through wired conection  on Ubuntu. wired network gets established but no internet available  (windows PC works with the same cable).

/sbin/route returns
Destination Gateway Genmask Flags Metric Ref Use Iface
default     77.70.103.1 0.0.0.0       UG 0 0 0 eth0
77.70.103.0 *           255.255.255.0 U  1 0 0 eth0
link-local  *           255.255.255.0 U 1000 0 0 eth0

I have tried mingling a bit with the configs (without manual set up of  IP address it does not connect to wirde network at all, with manual set  up of addresses it connects but no internet).

I am using TP-LINK TL-SF1008D as ethernet switch.
As I said the same cable works fine on a windows PC

Please help.

---

