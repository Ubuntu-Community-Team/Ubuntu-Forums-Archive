---
title: "hostname -f  and -s fails with &quot;hostname: Unknown host&quot; under 8.04.3 LTS"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by Angrysmiley on 2010-04-15
Hi,

I got an peculiar issue where hostname -f and hostname -s failes with "hostname: Unknown host",  whilst hostname works Ok and returns the value in /etc/hostname.

The release is 8.04.3 LTS,   ( I have used host.domain.com as an example but it reflects
the real life configuration ).  

Here is the output from:

/etc/hosts

127.0.0.1       localhost.localdomain localhost
10.42.10.10     host.domain.com  host

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


/etc/hostname

host.domain.com

/etc/resolv.conf

search domain.com
nameserver 10.40.10.30
nameserver 10.40.10.20

/etc/nsswitch.conf

asswd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


Any thoughts on why might be causing this?  DNS etc resolves OK btw.

---

### Post by jkd03d on 2010-06-21
I am having the same issue.  Did you ever resolve this?

---

### Post by Iowan on 2010-06-21
Still on 8.04.03? Current is (at least - haven't checked recently) 8.04.4.

---

