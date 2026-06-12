---
title: "Setting home network aliases?"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by goemonburo on 2009-10-18
I'm trying to set a few aliases for my machines in my home network.  This was easy using Fedora (I have several machines, one uses Ubuntu Intrepid) but I can't seem to find a tool that let's me map some network IP addresses to the appropriate alias names.

For example:

192.168.0.100, paris.mydomain
192.168.0.111, rome.mydomain
192.168.0.112, tokyo.mydomain


What's the appropriate tool for doing this or am I up the creek?  

I'm currently able to ssh to 192.168.0.100, etc., just fine.  I just want to type "ssh paris" instead.

Many thanks!

---

### Post by chili555 on 2009-10-18
I assume all the machines have static IPs. There are more elegant ways to do this that require downloaded packages and some configuration, but the kwik-n-EZ way to do it is to edit */etc/hosts* on the machine that will do the ssh to look like:```
127.0.0.1	localhost
127.0.1.1	username

192.168.0.100 paris
192.168.0.111 rome
192.168.0.112 tokyo

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```The .mydomain is unnecessary.

---

