---
title: "looking for ping receipt notification and possibly other network debugging info"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by Xnyper on 2009-12-05
I purchased some routers and switches to set up a lab with (studying for CCNA).  I also found an old laptop to use.  Initially all that I wanted to do is plug the laptop into one of my routers so that it will respond to PINGs.  I put 9.10 on it and now it does that just fine.

I was thinking though, that it would be cool if there were some way I could set it up to display the ping information when it got the PING.

I mean, if I get to see my desktop display this:

```
PING 192.168.1.109 (192.168.1.109) 56(84) bytes of data.
64 bytes from 192.168.1.109: icmp_seq=1 ttl=64 time=1.94 ms
64 bytes from 192.168.1.109: icmp_seq=2 ttl=64 time=0.836 ms
64 bytes from 192.168.1.109: icmp_seq=3 ttl=64 time=0.805 ms
```

Why can't my laptop display something like this:

```

Received 64 bytes from 192.168.1.113: icmp_seq=1 ttl=64 time=1.94 ms
Received 64 bytes from 192.168.1.113: icmp_seq=2 ttl=64 time=0.836 ms
Received 64 bytes from 192.168.1.113: icmp_seq=3 ttl=64 time=0.805 ms
```

I'm hoping somebody knows of some kind of network-debugging I can turn on to display this information.  Thanks!

---

