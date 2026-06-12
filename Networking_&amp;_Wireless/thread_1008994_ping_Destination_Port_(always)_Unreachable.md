---
title: "ping: Destination Port (always) Unreachable"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by Ludachrispeed on 2008-12-12
I'm kind of noobish, but I've given this one a good shot.

Every time I ping ANYTHING I get something like this:

```

$ ping -c 3 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
From yx-in-f100.google.com (74.125.45.100) icmp_seq=1 Destination Port Unreachable
From yx-in-f100.google.com (74.125.45.100) icmp_seq=2 Destination Port Unreachable
From yx-in-f100.google.com (74.125.45.100) icmp_seq=3 Destination Port Unreachable

--- google.com ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2008ms


```

I can ping my router... that works successfully.

BUT the router can't be the problem, because I unplugged it and am now connected straight to the wall.

Any help at all is greatly appreaciated!

- running Ubuntu 8.10
- Laptop = Dell Latitude

---

### Post by Ludachrispeed on 2008-12-13
Turns out I can ping just fine from anywhere but my appartment... I guess that means there is some router for the appartment building that denies or rejects ICMP echo requests.

Does anyone know a way around that? 'course it's not important... or at least it wasn't until I found out that I can't do it.

---

### Post by lensman3 on 2008-12-13
Try 

 /usr/sbin/tracepath google.com

Tracepath does MTU discovery and sends udp packets which can't be blocked (usually).  It will display all the routers in between your machine and the destination.  The M$ version is called "tracert" but uses TCP and special ports (which can be blocked).  tracepath can also tell you if the forward path is the same as the return path.

Enjoy.

---

### Post by Ludachrispeed on 2008-12-14
Thanks!

Tracepath revealed that there are two hops past my router that I can ping.  The next hop is some computer that apparently denies lots of services, because after it tracepath only returns "no reply". I haven't found anything past it that I can ping.

Interesting!

Thank you for your idea.

---

### Post by reloweb on 2010-03-13
I have the same problem but I can't ping my router...
When I try to ping it, it give me this message:

```
reloaded@Iuvenis:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=1 Destination Port Unreachable
From 192.168.0.2 icmp_seq=2 Destination Port Unreachable
From 192.168.0.2 icmp_seq=3 Destination Port Unreachable
From 192.168.0.2 icmp_seq=4 Destination Port Unreachable
^C
--- 192.168.0.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3000ms
```

---

