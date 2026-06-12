---
title: "alpine mail"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by johnh10000 on 2009-06-18
Hi gang b4 I make a BIG mistake, I'll ask first ;)

alpine recons that I haven't got a fully formed email addr fair:

johnh10000@tux

now I have an always on connection and have a resolveable ip namely
tux.isa-geek.org.

So me thinks if I change my hosts file a bit:

the current one:

127.0.0.1       localhost
#127.0.1.1      tux
127.0.0.1       localhost.localdomain   localhost
#127.0.0.1      tux mail.tux.isa-geek.org ftp.tux.isa-geek.org

# [www.tux.isa-geek](www.tux.isa-geek)
192.168.1.1     router
192.168.1.3     tux tux.isa-geek.org

######################
# would changing the order here work????????????????????????????????????
#####################################

192.168.1.2     lounge
192.168.1.40    bedroom

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
-------------------------

If not how can I persuade it?

---

