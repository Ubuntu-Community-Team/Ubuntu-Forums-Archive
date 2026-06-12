---
title: "DNS problem 10.04 / 10.10"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by seamuso on 2011-01-31
If I ping from one machine to another using only the hostname, I get a correct response and the complete name from DNS shows in the results -

```
seamuso@big-blue:~$ ping blue-web
PING blue-web.bfcs.local (192.168.1.7) 56(84) bytes of data.
64 bytes from blue-web.bfcs.local (192.168.1.7): icmp_req=1 ttl=64 time=0.785 ms
64 bytes from blue-web.bfcs.local (192.168.1.7): icmp_req=2 ttl=64 time=0.770 ms
64 bytes from blue-web.bfcs.local (192.168.1.7): icmp_req=3 ttl=64 time=0.098 ms
```

If I ping complete domain name on the other hand - 

```
 seamuso@big-blue:~$ ping blue-web.bfcs.local
ping: unknown host blue-web.bfcs.local
```

if I run a dig on the name, it's corrctly resolving -

```
; <<>> DiG 9.7.1-P2 <<>> blue-web.bfcs.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 39954
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;blue-web.bfcs.local.		IN	A

;; ANSWER SECTION:
blue-web.bfcs.local.	1500	IN	A	192.168.1.7

;; AUTHORITY SECTION:
bfcs.local.		1500	IN	NS	blue-store.bfcs.local.
bfcs.local.		1500	IN	NS	blue-toshiba.bfcs.local.
bfcs.local.		1500	IN	NS	blue-crm2.bfcs.local.

;; ADDITIONAL SECTION:
blue-crm2.bfcs.local.	1500	IN	A	192.168.1.5
blue-store.bfcs.local.	1500	IN	A	192.168.1.6
blue-toshiba.bfcs.local. 1500	IN	A	192.168.1.13

;; Query time: 0 msec
;; SERVER: 192.168.1.5#53(192.168.1.5)
;; WHEN: Mon Jan 31 12:06:59 2011
;; MSG SIZE  rcvd: 177
```

Now, if I do the same from any of the nameserver machines, everything returns correctly, including the full domain name of the machine - 

```
seamuso@blue-crm2:~$ ping blue-web.bfcs.local
PING blue-web.bfcs.local (192.168.1.7) 56(84) bytes of data.
64 bytes from blue-web.bfcs.local (192.168.1.7): icmp_seq=1 ttl=64 time=1.53 ms
64 bytes from blue-web.bfcs.local (192.168.1.7): icmp_seq=2 ttl=64 time=0.798 ms
64 bytes from blue-web.bfcs.local (192.168.1.7): icmp_seq=3 ttl=64 time=0.276 ms
```

This is only happening on my ubuntu client machines .. xp and win7 clients are working correctly.

The 4 systems affected are running 10.04lts (3 systems) and 10.10. Any ideas on what might be causing this so I can correct it?

Here are the basic config files for the machine I ran the example tests from. The setups (save IP addresses and names) are the same across all of the machines (.

resolv.conf -

```
domain bfcs.local
search bfcs.local
nameserver 192.168.1.5
nameserver 192.168.1.6
```

/etc/hosts -
```
127.0.0.1       localhost.localdomain   localhost
192.168.1.8     big-blue.bfcs.local     big-blue
```

hostname info -

```
root@big-blue:~# hostname
big-blue.bfcs.local
root@big-blue:~# hostname -f
big-blue.bfcs.local
```

Sorted it out when I was looking for other things that might be causing the problem. It turned out to be avahi.

---

### Post by Iowan on 2011-01-31
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? ;)

---

### Post by seamuso on 2011-01-31
> **Iowan said:**
> [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? ;)

:lolflag: went on with my business, had set the title to solved ... missed the resolved buitton.

---

