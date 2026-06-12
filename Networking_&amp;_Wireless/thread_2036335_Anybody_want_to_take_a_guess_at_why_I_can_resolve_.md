---
title: "Anybody want to take a guess at why I can resolve DNS names but cannot ping them?"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by tay9000 on 2012-08-01
I am using Ubuntu 12.04 LTS and I have my DNS server set to 192.168.0.18 which is a FreeBSD server running BIND. My other hosts are able to ping taynet.local (192.168.0.58), however my Ubuntu desktop can not. I get "unknown host taynet.local." But when I dig taynet.local, it resolves to 192.168.0.58 as it should but I can not ping by DNS name. However, I can ping it by IP so I know it is not a firewall issue (not on the remote hosts anyway) and on top of that I can't ping any of the other hostnames on my network. However, I can ping names like youtube.com, google.com, apache.org, etc. It just seems to be things on my LAN I can not ping by DNS names from my Ubuntu desktop. I tried setting the search domain setting to "taynet.local" but that didn't help. Any thoughts on what else I can try? This seems like a really weird issue to me. Ubuntu is definitely not my strong point. :)

[COLOR="DarkGreen"]tay@tay-desktop:~$ dig taynet.local[/COLOR]
```

; <<>> DiG 9.8.1-P1 <<>> taynet.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41651
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;taynet.local.			IN	A

;; ANSWER SECTION:
taynet.local.		3600	IN	A	192.168.0.58

;; AUTHORITY SECTION:
taynet.local.		3600	IN	NS	yamagi.taynet.local.

;; ADDITIONAL SECTION:
yamagi.taynet.local.	3600	IN	A	192.168.0.18

;; Query time: 1 msec
;; SERVER: 192.168.0.18#53(192.168.0.18)
;; WHEN: Wed Aug  1 12:49:28 2012
;; MSG SIZE  rcvd: 83

```
[COLOR="DarkGreen"]tay@tay-desktop:~$ ping taynet.local[/COLOR]
```
ping: unknown host taynet.local
```
[COLOR="DarkGreen"]tay@tay-desktop:~$ ping yamagi.taynet.local[/COLOR]
```
ping: unknown host yamagi.taynet.local
```
[COLOR="DarkGreen"]tay@tay-desktop:~$ ping 192.168.0.58[/COLOR]
```
PING 192.168.0.58 (192.168.0.58) 56(84) bytes of data.
64 bytes from 192.168.0.58: icmp_req=1 ttl=64 time=0.356 ms
^C
--- 192.168.0.58 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.356/0.356/0.356/0.000 ms
```
[COLOR="DarkGreen"]tay@tay-desktop:~$ ping 192.168.0.18[/COLOR]
```
PING 192.168.0.18 (192.168.0.18) 56(84) bytes of data.
64 bytes from 192.168.0.18: icmp_req=1 ttl=64 time=0.276 ms
^C
--- 192.168.0.18 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.276/0.276/0.276/0.000 ms
```
[COLOR="DarkGreen"]tay@tay-desktop:~$ ping youtube.com[/COLOR]
```
PING youtube.com (74.125.239.0) 56(84) bytes of data.
64 bytes from lax04s09-in-f0.1e100.net (74.125.239.0): icmp_req=1 ttl=52 time=26.5 ms
^C
--- youtube.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 26.511/26.511/26.511/0.000 ms
```
[COLOR="DarkGreen"]tay@tay-desktop:~$ ping apache.org[/COLOR]
```
PING apache.org (192.87.106.229) 56(84) bytes of data.
64 bytes from aurora-2012.apache.org (192.87.106.229): icmp_req=1 ttl=40 time=182 ms
64 bytes from aurora-2012.apache.org (192.87.106.229): icmp_req=2 ttl=40 time=203 ms
^C
--- apache.org ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 182.412/193.011/203.611/10.608 ms
```
[COLOR="DarkGreen"]tay@tay-desktop:~$ ifconfig[/COLOR]
```
eth0      Link encap:Ethernet  HWaddr 00:19:21:e5:48:7a  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fee5:487a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1842028 (1.8 MB)  TX bytes:308505 (308.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50587 (50.5 KB)  TX bytes:50587 (50.5 KB)
```

---

### Post by andrewc6l on 2012-08-01
The only thing I can think might be a possibility is that your /etc/resolv.conf doesn't have the right nameserver line? If that's the case, not sure how dig is finding it though...

---

### Post by tay9000 on 2012-08-01
> **andrewc6l said:**
> The only thing I can think might be a possibility is that your /etc/resolv.conf doesn't have the right nameserver line? If that's the case, not sure how dig is finding it though...
[COLOR="DarkGreen"]tay@tay-desktop:~$ cat /etc/resolv.conf [/COLOR]
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search taynet.local
```

When I first posted, I had it hard set in resolv.conf to 192.168.0.18 in case you were wondering. Either way, it still can't get to the hosts using DNS names. This is really baffling to me. If you can ping the IP and resolve its DNS name, you should be able to ping it by hostname. There has got to be some little Ubuntu quirk that I don't know about. By the way, I also have a Debian server on my network and it doesn't have this problem. And my understanding is Ubuntu is Debian based so????? Btw if it makes a difference, I am running Ubuntu with the Gnome GUI I think. Whatever the Live Desktop version comes standard with. I normally don't use Linux with a GUI so I'm not sure exactly what it is that I am running haha.

[COLOR="DarkGreen"]tay@tay-desktop:~$ arp[/COLOR]
```
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.1              ether   b8:e6:25:30:ad:01   C                     eth0
yamagi.taynet.localhost  ether   00:1d:7d:25:ef:a5   C                     eth0
192.168.0.58             ether   00:24:8c:05:a9:b7   C                     eth0
```
[COLOR="DarkGreen"]tay@tay-desktop:~$ ping yamagi.taynet.localhost[/COLOR]
```
ping: unknown host yamagi.taynet.localhost
```

---

### Post by Selfish Meme on 2012-08-09
After I had the same problem I did some Googling and found the solution, it has to do with the search order in the new resolver

[http://www.woofpuppy.com/2012/05/solving-local-dns-resolution-problems.html](http://www.woofpuppy.com/2012/05/solving-local-dns-resolution-problems.html)

adjust the search order in /etc/nsswitch.conf. To do this:

Edit /etc/nsswitch.conf and change the following line:
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
To:
hosts: files dns mdns4_minimal [NOTFOUND=return] mdns4
And save your changes. Now, test ping one of your .local host names to verify the change has taken effect as expected.

---

### Post by papibe on 2012-08-09
Hi tay9000.

It looks like a conflict with avahi-daemon.

Are you running it? Test it like this:
```
ps aux | grep -i avahi
```
Try stopping the service and let us know how it goes:
```
sudo service avahi-daemon stop
```
Regards.

---

