---
title: "rsh without password required"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by loran on 2006-05-01
I am attempting to rlogin or rsh into a networked Redhat Enterprise ver 4 box.  The vendor of the Redhat box requires that I be able to rsh or rlogin without needing to enter a password for the activities I am attempting.  I have modified the etc/hosts, etc/hosts.equiv, etc/hosts.allow, .rhosts, and etc/securetty files on the Redhat box to include my local hostname and have also tried connecting using IP addressing instead of hostname but I am always asked for a password.
Also, how does one vi the etc/hosts.allow file on Ubuntu machines?  Nothing I have tried seems to work (including sudo vi and using :set noro while in the vi program)

---

