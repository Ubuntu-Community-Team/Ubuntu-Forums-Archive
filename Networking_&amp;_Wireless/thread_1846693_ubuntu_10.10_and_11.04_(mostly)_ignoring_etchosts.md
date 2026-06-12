---
title: "ubuntu 10.10 and 11.04 (mostly) ignoring /etc/hosts"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by Paul from VA on 2011-09-19
Hi all,

I'm a grizzled linux veteran (used Debian for many years before installing ubuntu, and Corel Linux before that), but I've hit a problem that's stumping me.  I'm trying to use SSH tunelling to use some research software off-campus, so I pretend that my computer is the license manager server.

My /etc/hosts looks like this:
> 192.168.160.252	luminiferous	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	luminiferous	localhost6.localdomain6	localhost6
127.0.1.1	luminiferous
127.0.0.1	lm1.license.Virginia.EDU
#127.0.1.1	lm2.license.Virginia.EDU
#127.0.1.1       lm3.license.Virginia.EDU

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


/etc/host.conf:
> 
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on


/etc/nsswitch.conf:
> # /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


Yes, I've tried the carriage return in the hosts file.  Here's the only clue that I have.  If I do 'ping lm1.license.virginia.edu' it resolves to 127.0.0.1 like I want.  If I do 'ping lm1.license.virginia.edu.', it resolves to the real IP.  Using the hosts and nslookup commands both return the ip address that is not localhost.

Can anyone tell my why the entry in /etc/hosts isn't taking precedence over the name server?

Cheers,

----Paul

---

### Post by bab1 on 2011-09-19
> **Paul from VA said:**
> Hi all,

I'm a grizzled linux veteran (used Debian for many years before installing ubuntu, and Corel Linux before that), but I've hit a problem that's stumping me.  I'm trying to use SSH tunelling to use some research software off-campus, so I pretend that my computer is the license manager server.

My /etc/hosts looks like this:


/etc/host.conf:


/etc/nsswitch.conf:


Yes, I've tried the carriage return in the hosts file.  Here's the only clue that I have.  If I do 'ping lm1.license.virginia.edu' it resolves to 127.0.0.1 like I want.  If I do 'ping lm1.license.virginia.edu.', it resolves to the real IP.  Using the hosts and nslookup commands both return the ip address that is not localhost.

Can anyone tell my why the entry in /etc/hosts isn't taking precedence over the name server?

Cheers,

----Paul
The commands *host * and *nslookup ***only work **with DNS servers.  The /etc/hosts file is never queried with these DNS tools.

---

### Post by Paul from VA on 2011-09-19
D'oh!  Thanks!  I had assumed hosts was for all name resolution, not just dns.  I'll mark this as resolved.....

---

