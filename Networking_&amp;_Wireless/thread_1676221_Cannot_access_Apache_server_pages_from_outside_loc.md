---
title: "Cannot access Apache server pages from outside local network"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by mahimahi42 on 2011-01-26
Hello all,

I'm trying to setup an Apache webserver on my computer in order to practice HTML5/CSS3 for an upcoming competition I'm in. I'm able to access my site from inside my network, but I cannot outside my network. I've had several people try, and they all report that the server just times out. I'm running Ubuntu 10.04 and Apache 2.2.17

My site is at [http://mahimahi42.dyndns.org](http://mahimahi42.dyndns.org)

Here is the output of ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:26:22:50:0f:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 

eth1      Link encap:Ethernet  HWaddr 0c:60:76:61:96:d6  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe61:96d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1016056 errors:0 dropped:0 overruns:0 frame:4255336
          TX packets:681885 errors:83 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1251500993 (1.2 GB)  TX bytes:191255607 (191.2 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45203 (45.2 KB)  TX bytes:45203 (45.2 KB)

```

EDIT: I have forwarded port 80 to the box with Apache, and setup DynDns on my router (Netgear WPN824v2)

---

### Post by arvevans on 2011-01-26
Do you have an active firewall between your LAN and the Internet?  If so you will need to open port 80 so that outsiders can see your web server.
[INDENT]
arv@arv-desktop:~$ traceroute mahimahi42.dyndns.org
traceroute to mahimahi42.dyndns.org (98.166.153.202), 30 hops max, 60 byte packets
 1  172.16.0.254 (172.16.0.254)  23.646 ms  24.499 ms  25.330 ms
 2  boid-dsl-gw04-196.boid.qwest.net (184.99.64.196)  54.818 ms  59.916 ms  60.737 ms
 3  184-99-65-25.boid.qwest.net (184.99.65.25)  62.648 ms  63.475 ms  64.361 ms
 4  sea-brdr-02.inet.qwest.net (67.14.41.14)  92.153 ms  94.599 ms  99.642 ms
 5  te8-3-10G.ar5.SEA1.gblx.net (64.208.110.141)  107.080 ms  109.575 ms  112.039 ms
 6  COXCOM-INC.te6-3.ar3.DCA3.gblx.net (67.17.134.46)  174.559 ms  145.205 ms  139.857 ms
 7  nrfkdsrj01-ae0.0.rd.hr.cox.net (68.1.0.25)  156.409 ms  162.420 ms nrfkdsrj02-ae0.0.rd.hr.cox.net (68.1.0.27)  152.286 ms
 8  * * *
 9  * * *
10  pavbsysr01-atm141202.hr.hr.cox.net (68.10.8.98)  164.681 ms  179.672 ms  182.185 ms
11  * * *
12  * * *
[/INDENT]

It appears that the DNS redirection is working, but that there is no response to HTTP calls from your IP address.

---

### Post by mahimahi42 on 2011-01-26
I don't believe so, though I'll double-check. I think a Windows machine has a firewall for that box, but I doubt that would affect anything. I'll recheck my router's settings.

---

### Post by arvevans on 2011-01-26
If your IP address is not 98.166.153.202, then the dyndns redirect is not primed properly.  Make sure that your router is actually registering the current IP address with dyndns.

[INDENT]arv@arv-desktop:~$ dig mahimahi42.dyndns.org

; <<>> DiG 9.7.1-P2 <<>> mahimahi42.dyndns.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33066
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mahimahi42.dyndns.org.		IN	A

;; ANSWER SECTION:
mahimahi42.dyndns.org.	60	IN	A	98.166.153.202

;; Query time: 305 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Wed Jan 26 19:18:13 2011
;; MSG SIZE  rcvd: 55

arv@arv-desktop:~$ ping 98.166.153.202
PING 98.166.153.202 (98.166.153.202) 56(84) bytes of data.
^C
--- 98.166.153.202 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4031ms

[/INDENT]

---

### Post by mahimahi42 on 2011-01-26
According to DynDNS that is the IP address it redirects to. As for my router, there's a tab labeled 'Dynamic DNS' that asks for the DNS provider (DynDNS being the only option), the host name, and my DynDNS username and password.

For the host name, I do put in the [http://mahimahi42.dyndns.org](http://mahimahi42.dyndns.org), correct?

---

