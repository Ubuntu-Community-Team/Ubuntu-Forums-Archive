---
title: "Recent upgrades degrade online performance -- Help!"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by bw44 on 2009-06-12
I've been running Hardy Heron since it came out and have always applied Synaptic upgrades as they were destributed.  Following those released and applied June 9, my wireless connection to the Internet has degraded to the point I can't use it, although it will sometimes connect and allow intermittent slow communication.  Firefox, Skype and Thunderbird are all equally affected.

I have a dual-boot Windows XP system (also up-to-date) and it is not experiencing ANY connectivity problems using the same wireless connection.

Here is the log of the changes I applied on June 9, 2009; can anyone suggest what upgrade might affect my wireless connection and how to back it out?

```
Commit Log for Tue Jun  9 08:22:13 2009

Upgraded the following packages:
imagemagick (7:6.3.7.9.dfsg1-2ubuntu1) to 7:6.3.7.9.dfsg1-2ubuntu1.1
libmagick10 (7:6.3.7.9.dfsg1-2ubuntu1) to 7:6.3.7.9.dfsg1-2ubuntu1.1
linux-headers-2.6.24-24 (2.6.24-24.53) to 2.6.24-24.54
linux-headers-2.6.24-24-generic (2.6.24-24.53) to 2.6.24-24.54
linux-image-2.6.24-24-generic (2.6.24-24.53) to 2.6.24-24.54
linux-libc-dev (2.6.24-24.53) to 2.6.24-24.54
linux-restricted-modules-2.6.24-24-generic (2.6.24.17-24.1) to 2.6.24.18-24.1
linux-restricted-modules-common (2.6.24.17-24.1) to 2.6.24.18-24.1
lsb-base (3.2-4ubuntu1) to 4.0-0ubuntu0.8.04.1
lsb-release (3.2-4ubuntu1) to 4.0-0ubuntu0.8.04.1

```

Just in case there is some kind of cumulutive interaction of recent changes, here are the most recent commit log entries prior to the above:
```

Commit Log for Sat Jun  6 17:24:00 2009

Installed the following packages:
gnucash-docs (2.2.0-1)

Commit Log for Fri Jun  5 09:34:06 2009

Upgraded the following packages:
file (4.21-3ubuntu1) to 4.21-3ubuntu2
installation-report (2.31ubuntu1) to 2.31ubuntu2
libmagic1 (4.21-3ubuntu1) to 4.21-3ubuntu2
libparted1.7-1 (1.7.1-5.1ubuntu9.1) to 1.7.1-5.1ubuntu9.2
parted (1.7.1-5.1ubuntu9.1) to 1.7.1-5.1ubuntu9.2

Commit Log for Wed Jun  3 22:03:55 2009

Installed the following packages:
gnucash (2.2.4-1ubuntu1)
gnucash-common (2.2.4-1ubuntu1)
guile-1.6 (1.6.8-6ubuntu1)
guile-1.6-slib (1.6.8-6ubuntu1)
libcrypt-ssleay-perl (0.55-1)
libdate-manip-perl (5.48-1)
libfinance-quote-perl (1.13-1)
libgoffice-0-4 (0.4.2-4)
libgoffice-0-common (0.4.2-4)
libgsf-gnome-1-114 (1.14.7-2ubuntu1)
libhtml-tableextract-perl (2.10-2)
libofx4 (1:0.9.0-2ubuntu1)
libosp5 (1.5.2-3ubuntu3)
psfontmgr (0.11.10-0.2)
slib (3a4-4)

```
Sorry for the long post, but I have no idea where to begin debugging this problem, and since the it only showed up after applying the June 9 upgrade, I thought it must have something to do with that.  But what?

---

