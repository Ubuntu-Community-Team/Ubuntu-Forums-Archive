---
title: "dig trying to connect to 127.0.0.1, which is not in /etc/resolv.conf"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by knatten on 2009-04-26
I cannot resolve any hosts on one of my Ubuntu boxes.

```

$ cat /etc/resolv.conf 
193.75.75.75
193.75.75.193

```

These are the correct nameservers, which work on all my other boxes. When running "strace -f dig google.com", I can see it trying to sendmsg() to 127.0.0.1. For comparison, I checked strace on my other boxes, they sendmsg() to 193.75.75.75.

strace also tells me that dig indeed reads /etc/resolv.conf.

I do not have a .digrc.

The problem is not dig specific, it happens in all applications that need to resolve hosts.

The network works fine when I use IPs instead of hosts, and for hosts in /etc/hosts

I have tried to uninstall NetworkManager (network is set up in /etc/network/interfaces), but it did not help.


Full strace here: [http://knatten.org/paste/dig-problems.txt](http://knatten.org/paste/dig-problems.txt)


Any ideas are highly appreciated.

---

### Post by knatten on 2009-04-28
Some more info:

I do not have any dns-servers installed. I have confirmed with nmap that nothing listens on port 53.

I have confirmed with tcpdump that connections are attempted (and fail) to localhost when i do dig:
```

# tcpdump -i lo
20:40:39.973137 IP localhost.54342 > localhost.domain: 26332+ A? db.no. (23)
20:40:39.973179 IP localhost > localhost: ICMP localhost udp port domain unreachable, length 59
20:40:40.973157 IP6 ip6-localhost.36856 > ip6-localhost.domain: 26332+ A? db.no. (23)
20:40:40.973195 IP6 ip6-localhost > ip6-localhost: ICMP6, destination unreachable[|icmp6]
```

---

