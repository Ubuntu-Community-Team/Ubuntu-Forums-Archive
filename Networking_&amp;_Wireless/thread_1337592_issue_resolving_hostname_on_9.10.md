---
title: "issue resolving hostname on 9.10"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by iprolonged on 2009-11-25
hi all, recently upgraded to 9.10, Internet has been flaky ever since.

I'm using the connection now (Win XP notebook), so I know that's OK.

hosts and hostname as follows:

cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 scanlon-machine

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/hostname
scanlon-machine

Any suggestions as to where I should start looking?

Cheers.

---

### Post by rudy.b on 2009-11-26
What specifically do you mean by your "Internet has been flaky?"

---

### Post by Sslaxx on 2009-11-26
Name resolution appears to be achingly slow and causing time-outs at random, for a start.

iprolonged, check [http://ubuntuforums.org/showthread.php?t=1304547](http://ubuntuforums.org/showthread.php?t=1304547) out if you haven't already, see if anything in there may help.

---

### Post by Iowan on 2009-11-26
Check */etc/resolv.conf* to verify a valid DNS source.

---

### Post by Sslaxx on 2009-11-26
> **Iowan said:**
> Check */etc/resolv.conf* to verify a valid DNS source.
The only problem with that is Network Manager...

---

