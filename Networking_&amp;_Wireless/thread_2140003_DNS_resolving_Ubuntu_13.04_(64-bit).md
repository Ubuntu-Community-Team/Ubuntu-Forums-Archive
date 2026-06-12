---
title: "DNS resolving Ubuntu 13.04 (64-bit)"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by Justgivemeaname on 2013-04-28
Hi everybody,

First of all, this is my first post, since I managed to solve all other problems I ever had using Ubuntu by other post on this forum (Thanks for that by the way!), but this time I didn't find the solution, so if the post in the wrong location: sorry!

After a fresh install of Ubuntu Desktop 13.04 (64-bit) on a pc that previously had Ubuntu 12.10 installed, my DNS resolving is giving some strange issues. In short, I can't ping a host name of an internal device, but I can ping the ip address. This only happens internally, so pinging [www.google.com]("http://www.google.com") or 173.194.78.99 works OK. In the morning, before the upgrade, it worked perfectly and after the upgrade, it doesn't work at all.

I've got a home server running Ubuntu Server 12.04.2 LTS OS with two virtual machines: dns1 (primary master) and dns2 (secondary master), both are using Bind9 for internal DNS resolving and caching, also running Ubuntu Server 12.04.2 LTS.
Both the servers are working without issues, since on other devices (Windows, Android, Ubuntu) resolving and pinging an internal host name is working OK.

Here is an overview of my dns database on the primary master dns server:
```
        
IN      NS      dns1.home.local.
IN      NS      dns2.home.local.

dns1            IN      A       10.19.91.20
dns2            IN      A       10.19.91.21

router          IN      A       10.19.91.1
homeserver      IN      A       10.19.91.2
mypc-lan        IN      A       10.19.91.62
mypc-wifi       IN      A       10.19.91.92

```

And here is an overview of my network configuration on the pc with the issues:
```

me@mypc:~# nm-tool


NetworkManager Tool


- Device: eth0  [Thuisverbinding] ----------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        **:*:**:**:**:**


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.19.91.62
    Prefix:          24 (255.255.255.0)
    Gateway:         10.19.91.1


    DNS:             10.19.91.20
    DNS:             10.19.91.21
    DNS:             62.179.104.196 (DNS of my ISP)

```

So what actually happens is:
```

me@mypc:~$ ping 10.19.91.1
PING 10.19.91.1 (10.19.91.1) 56(84) bytes of data.
64 bytes from 10.19.91.1: icmp_req=1 ttl=64 time=0.564 ms
64 bytes from 10.19.91.1: icmp_req=2 ttl=64 time=0.641 ms
64 bytes from 10.19.91.1: icmp_req=3 ttl=64 time=0.647 ms
64 bytes from 10.19.91.1: icmp_req=4 ttl=64 time=0.621 ms
^C
--- 10.19.91.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.564/0.618/0.647/0.037 ms

```
```

me@mypc:~$ ping router.home.local
ping: unknown host router.home.local

```

But it seems that resolving the DNS zone works fine, as can be seen here:
```

me@mypc:~$ dig router.home.local

; <<>> DiG 9.9.2-P1 <<>> router.home.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20969
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 3


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;router.home.local.        IN    A


;; ANSWER SECTION:
router.home.local.    604800    IN    A    10.19.91.1


;; AUTHORITY SECTION:
home.local.        604800    IN    NS    dns1.home.local.
home.local.        604800    IN    NS    dns2.home.local.


;; ADDITIONAL SECTION:
dns1.home.local.    604800    IN    A    10.19.91.20
dns2.home.local.    604800    IN    A    10.19.91.21


;; Query time: 1 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sun Apr 28 16:23:11 2013
;; MSG SIZE  rcvd: 132

```

(I already changed some settings to replace ;;SERVER: 127.0.1.1#53(127.0.1.1) with ;;SERVER: 10.19.91.20#53, but this didn't solve anything.)

Using the *host* command gives the expected results:
```

me@mypc:~$ host router.home.local
router.home.local has address 10.19.91.1
me@mypc:~$ host 10.19.91.1
1.91.19.10.in-addr.arpa domain name pointer router.home.local

```

What I think is really strange is that I can ***sometimes*** ping router (without .home.local) after I add the search domain through the Network Manager tool, which doesn't work anymore after a reboot:
```

me@mypc:~# ping router
PING router.home.local (10.19.91.1) 56(84) bytes of data.
64 bytes from router.home.local (10.19.91.1): icmp_req=1 ttl=64 time=0.698 ms
64 bytes from router.home.local (10.19.91.1): icmp_req=2 ttl=64 time=0.651 ms
64 bytes from router.home.local (10.19.91.1): icmp_req=3 ttl=64 time=0.597 ms
64 bytes from router.home.local (10.19.91.1): icmp_req=4 ttl=64 time=0.523 ms
^C
--- router.home.local ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 0.523/0.617/0.698/0.067 ms

```

This is where I get stuck and I'm hoping that somebody is able to help me with this.
Sorry for the long post. :)

Thanks!

---

### Post by chrisguk on 2013-05-02
Sorry to hijack the post.  Im having the same problems though I did notice that the the nameservers data and dns-search are no longer being appended to the resolv.conf anymore.  Im trying to find a work around, but would be grateful for anyone that has a fix for this?

---

### Post by guusb on 2013-05-14
I also have this problem. I found this thread [http://ubuntuforums.org/showthread.php?t=2001913](http://ubuntuforums.org/showthread.php?t=2001913) which sounds like it might be the solution.
I didn't have the chance to try it yet.

---

