---
title: "Can't access to some domains"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by nandelbosc on 2010-10-30
From yesterday I'm experiencing the most estrange problem for over 6 years that I'm sysadmin... and it's happening to me at my home!

Here the problem

Ping to google.com works ok...
```
$ ping www.google.com
PING www.l.google.com (66.249.92.104) 56(84) bytes of data.
64 bytes from par03s01-in-f104.1e100.net (66.249.92.104): icmp_req=1 ttl=52 time=69.2 ms
64 bytes from par03s01-in-f104.1e100.net (66.249.92.104): icmp_req=2 ttl=52 time=69.0 ms
^C64 bytes from par03s01-in-f104.1e100.net (66.249.92.104): icmp_req=3 ttl=52 time=69.3 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 69.095/69.244/69.342/0.107 ms

```

Ping to ubuntu.com works ok...
```
$ ping www.ubuntu.com
PING www.ubuntu.com (91.189.89.88) 56(84) bytes of data.
64 bytes from privet.canonical.com (91.189.89.88): icmp_req=1 ttl=49 time=72.9 ms
64 bytes from privet.canonical.com (91.189.89.88): icmp_req=2 ttl=49 time=72.7 ms
64 bytes from privet.canonical.com (91.189.89.88): icmp_req=3 ttl=49 time=72.4 ms
64 bytes from privet.canonical.com (91.189.89.88): icmp_req=4 ttl=49 time=71.6 ms
^C
--- www.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 71.690/72.483/72.997/0.492 ms
```

Ping to 1and1.es don't work!
```
$ ping www.1and1.es
PING www.1and1.es (212.227.133.6) 56(84) bytes of data.
^C
--- www.1and1.es ping statistics ---
55 packets transmitted, 0 received, 100% packet loss, time 54022ms

```

again...
```
$ ping www.1and1.es
PING www.1and1.es (212.227.133.6) 56(84) bytes of data.
^C
--- www.1and1.es ping statistics ---
19 packets transmitted, 0 received, 100% packet loss, time 18001ms

```

Ping to one of my domain in 1and1 don't work (the IP Address is resolved correctly)...
```
$ ping www.elseudomini.net
PING www.elseudomini.net (82.165.130.250) 56(84) bytes of data.
^C
--- www.elseudomini.net ping statistics ---
19 packets transmitted, 0 received, 100% packet loss, time 18004ms

```

I try to traceroute to my domain...
```
$ traceroute www.elseudomini.net
traceroute to www.elseudomini.net (82.165.130.250), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  0.366 ms  0.437 ms  0.509 ms
 2  89.128.192.1 (89.128.192.1)  34.606 ms  35.337 ms  37.262 ms
 3  * * *
 4  85.63.217.221 (85.63.217.221)  54.000 ms  55.684 ms  57.394 ms
 5  ge-5-0-0-0.madcr2.Madrid.opentransit.net (193.251.255.213)  59.319 ms  60.065 ms  61.789 ms
 6  po1-101-10G.ar2.MAD1.gblx.net (64.215.195.9)  63.519 ms  43.315 ms  43.376 ms
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

I'm using google DNS (8.8.8.8 ), I tried to change it to another (telefonica DNS: 80.58.32.97) with the same result.

I thought, perhaps from one and one, have public IP blocked, but the funny thing is that from another PC that I have at same room (with Ubuntu 10.04 too) connected to the same internet connection (with the same public IP Address) works perfectly!

I've run out of ideas. What else can I check???

---

### Post by toczek on 2011-03-02
I have the same problem.

Have you solved it?

---

### Post by nandelbosc on 2011-03-02
Hi toczek,

I'm sorry, but i can't remember what was the solution!

May re-install the system solve the problem because around that time I change the computer, but as I say, I'm not sure.

I can't help you much more... :(

---

### Post by berdy on 2011-04-24
I have the same problem...

---

### Post by dineshs on 2011-04-25
Will it be a problem with [MTU]("http://ubuntuforums.org/showthread.php?t=872346") ?

---

