---
title: "Slow lan connection?"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by bazuka666 on 2011-07-08
Hi people i know this is not the 1st post for slow connection under ubuntu 10.04...

but i have a probl with not only internet connection, i have a probl with local lan connection, i dont know how to fix it i have tried everything, dissable ipv6 etc...

when i copy via lan max speed is 3kb???!!! yea 3kb people, and my lan is 1gb

pls could any1 gimme some hints im loosing my nervs here, i tried 10.4, 10.10, 11.04 and with all os's i had the same probl... 
i dont know is it the probl with motherboard, but i dont have any probl under win7 x64

my config:
intel i7 2600k
gigabyte p67a-ud4-b3 (f3 bios)
16gb kingston
etc...

---

### Post by SoftwareExplorer on 2011-07-08
Ok, lets do some troubleshooting. Post the output of the following:

```
ping -c 10 he.net
ping -c 10 -n 216.218.186.2
ping6 he.net -c 10
ping6 -c 10 -n 2001:470:0:76::2
dig aaaa he.net
dig a he.net
```

With 'ping -c 10 he.net' and 'ping -c 10 -n 216.218.186.2' see if there is a noticeable time increase between pings with the 'ping -c 10 he.net' version in comparison to 'ping -c 10 -n 216.218.186.2'. This is not the time listed at the end of the line but the lag between the lines showing up.

Edit: By the way, what are you transfering files to/from? A windows machine? Another Ubuntu machine using samba (windows compatible)? Or another Ubuntu machine using SFTP (not as easily windows compatible, but more reliable)?

---

### Post by bazuka666 on 2011-07-09
Hi and thx for reply,

the network computer is also ubuntu x64 11.04 (upgraded few days ago) but on that computer everything is working great, network, internet speed is full, etc... 

for samba ill have to check when i get home, its possible that i have already installed samba,

ill check the ping test asap

cheers

---

### Post by bazuka666 on 2011-07-09
here r results


~$ ping -c 10 he.net
PING he.net (216.218.186.2) 56(84) bytes of data.
64 bytes from he.net (216.218.186.2): icmp_seq=2 ttl=59 time=204 ms
64 bytes from he.net (216.218.186.2): icmp_seq=4 ttl=59 time=190 ms
64 bytes from he.net (216.218.186.2): icmp_seq=5 ttl=59 time=207 ms
64 bytes from he.net (216.218.186.2): icmp_seq=6 ttl=59 time=199 ms
64 bytes from he.net (216.218.186.2): icmp_seq=7 ttl=59 time=191 ms
64 bytes from he.net (216.218.186.2): icmp_seq=8 ttl=59 time=217 ms
64 bytes from he.net (216.218.186.2): icmp_seq=10 ttl=59 time=189 ms

--- he.net ping statistics ---
10 packets transmitted, 7 received, 30% packet loss, time 17550ms
rtt min/avg/max/mdev = 189.770/200.233/217.125/9.496 ms
-------------------------------------

~$ ping -c 10 -n 216.218.186.2
PING 216.218.186.2 (216.218.186.2) 56(84) bytes of data.
64 bytes from 216.218.186.2: icmp_seq=1 ttl=59 time=209 ms
64 bytes from 216.218.186.2: icmp_seq=2 ttl=59 time=190 ms
64 bytes from 216.218.186.2: icmp_seq=3 ttl=59 time=203 ms
64 bytes from 216.218.186.2: icmp_seq=4 ttl=59 time=190 ms
64 bytes from 216.218.186.2: icmp_seq=5 ttl=59 time=200 ms
64 bytes from 216.218.186.2: icmp_seq=6 ttl=59 time=215 ms
64 bytes from 216.218.186.2: icmp_seq=7 ttl=59 time=430 ms
64 bytes from 216.218.186.2: icmp_seq=8 ttl=59 time=209 ms
64 bytes from 216.218.186.2: icmp_seq=9 ttl=59 time=189 ms
64 bytes from 216.218.186.2: icmp_seq=10 ttl=59 time=199 ms

--- 216.218.186.2 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9002ms
rtt min/avg/max/mdev = 189.348/223.810/430.478/69.433 ms

------------------------------------------
ping6 he.net -c 10
connect: Network is unreachable

ping6 -c 10 -n 2001:470:0:76::2
connect: Network is unreachable
------------------------------------------

~$ dig aaaa he.net

; <<>> DiG 9.7.0-P1 <<>> aaaa he.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7169
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;he.net.				IN	AAAA

;; ANSWER SECTION:
he.net.			86400	IN	AAAA	2001:470:0:76::2

;; Query time: 7 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Jul  9 21:55:22 2011
;; MSG SIZE  rcvd: 52

-------------------------------------------------------

~$ dig a he.net

; <<>> DiG 9.7.0-P1 <<>> a he.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64887
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;he.net.				IN	A

;; ANSWER SECTION:
he.net.			86400	IN	A	216.218.186.2

;; Query time: 7 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Jul  9 21:56:16 2011
;; MSG SIZE  rcvd: 40


hope this makes sense to u ;)

cheers

---

### Post by bazuka666 on 2011-07-09
i also notice that lan connection is dropping from time to time, but the lan icon shows everything ok???????

also max internet speed is 2mb and i have 4mb connection???

cheers

---

### Post by bazuka666 on 2011-07-10
I have just fixed the probl i had these days, and it was in lan driver r8169, so i switch to r8168 and everything is working now...

cheers

---

### Post by SoftwareExplorer on 2011-07-13
I'm glad you got it fixed, seeing how much help I was. :) I looked at the result of the tests and was having a hard time finding much. I kept thinking, "I'll try to figure out what to try next when I have free time."

---

### Post by SushiR on 2011-07-14
> **bazuka666 said:**
> I have just fixed the probl i had these days, and it was in lan driver r8169, so i switch to r8168 and everything is working now...

cheers

How exactly did you do it?

---

