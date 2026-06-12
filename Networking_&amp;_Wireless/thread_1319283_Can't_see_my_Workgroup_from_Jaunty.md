---
title: "Can't see my Workgroup from Jaunty"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by WildeBeest on 2009-11-08
My Jaunty machine can't see see my workgroup.

I have samba setup correctly.
I use the same configuration on Hardy and Karmic machines.

In nautilus they can see the workgroup, access each other including the Jaunty machine.
The Jaunty machine can't.

I've read through just about all of the threads dealing with samba.

when I execute the command: "sudo iptables -L" I get the following.

```
FATAL: Error inserting ip_tables (/lib/modules/2.6.28-14-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Cannot allocate memory
iptables v1.4.1.1: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

```

I think that this may be the source of my problem.

How do I fix that?

---

### Post by WildeBeest on 2009-11-09
ttt

---

### Post by Iowan on 2009-11-09
I got something similar when I (accidently) tried it without **sudo**...

---

