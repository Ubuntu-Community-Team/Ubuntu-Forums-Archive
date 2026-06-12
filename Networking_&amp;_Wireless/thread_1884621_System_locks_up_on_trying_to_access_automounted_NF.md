---
title: "System locks up on trying to access automounted NFS partitions."
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by jtappin on 2011-11-21
On my laptop (System 76 Pangolin P5), I have the NFS client set up to automount any NFS exports from the lab system using auto.net and mounting as /net/<host>/....

However for a while now if I try to open a a directory with Konqueror (or as I recall Firefox though I've not tried it recently), the system locks up completely--Mouse cursor does not move, clock and system monitors don't update and no keyboard response (I can't even reboot the system with Alt+SysRq+ R E I S U B).

The problem only occasionally happens from the command line in a Konsole terminal, and I've never seen it happen from the console.

The NFS servers are using NFS v3, as some of the systems on the lab network use Solaris 9 which doesn't have V4, and are running on a mixture of Solaris-Sparc, Solaris-X86_64 and Debian systems.

There are no related error messages in /var/log/syslog or /var/log/Xorg.0.log

The problem is seen on Natty and Oneiric, but did not occur on Maverick.

Does anyone have any pointers as to where to look next?

---

