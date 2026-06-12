---
title: "Trouble with ehcache and multicast on Ubuntu Lucid"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by JustinGordon on 2010-09-13
From the ehcache FAQ:
> The reason for the behavior might be that the java call: InetAddress.getLocalHost(); always returns the loopback address, which is 127.0.0.1. All you need to do is crack open the network config and make sure that the hostname of the machine returns a valid network address accessible by other peers on the network. 

Does anybody know how to do this on the most current Ubuntu Debian distro (Lucid)? 

Also, any best place for troubleshooting multicast configuration? I'm trying to get it working on a single linux machine with multiple JVMs. 

Thanks so much in advance. 

Regards, 

Justin

---

### Post by relay_man on 2010-09-13
Just a guess, but perhaps adding a line in etc/hosts?

---

### Post by JustinGordon on 2010-09-13
> **relay_man said:**
> Just a guess, but perhaps adding a line in etc/hosts?
Saying what?

I'm using DHCP, so I don't want to hardcode the address...

This is what I've got right now:
127.0.0.1	localhost
127.0.1.1	ahi

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Thanks in advance!

---

