---
title: "split routing - traceroute not displaying unrouted hops"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by fragtion on 2010-12-12
I recently switched my home server from debian lenny to ubuntu maverick. I've managed to port all my configs and stuff and so far I'm very happy.
There's one tiny thing that's griping me, that I never experienced before with debian's (older) packages/configuration...

Here's the situation:
My server dials up 2 pppoe (adsl) interfaces (different isp's) with split internet routes.

If I run a general traceroute to an internet IP, all the hops which are not routed via the same interface as the destination host/IP, will appear as "* * *" in the traceroute. This was never the case before and it would be preferred to see the IP's of all routers along the way regardless of whether they are routed... (I used to be able to see IP's like 10.0.0.x before through INTERNET traceroutes if they were hops along the way [IP's which would be unreachable if traced directly], and that's no longer the case) - isn't this kinda defeating the point of traceroute?

Here's an example:
Only ppp0 up, it is default gateway
```
root@pappasfw:/etc/ppp/peers# traceroute 196.24.33.35
traceroute to 196.24.33.35 (196.24.33.35), 30 hops max, 60 byte packets
 1  dsl-242-108-01.telkomadsl.co.za (41.242.108.1)  5.233 ms  6.335 ms  7.786 ms
** 2  196.43.11.202 (196.43.11.202)  9.428 ms  10.642 ms  11.826 ms**
 3  196.43.25.138 (196.43.25.138)  13.242 ms  14.213 ms  15.622 ms
 4  internet-solutions-gw.telkom-ipnet.co.za (196.25.46.90)  16.569 ms  18.000 ms  18.957 ms
 5  196.26.0.10 (196.26.0.10)  82.462 ms 168.209.1.170 (168.209.1.170)  82.237 ms 196.26.0.10 (196.26.0.10)  82.483 ms
 6  * * *
 7  jnb2-vl700-jnb1-vl700.net.tenet.ac.za (155.232.6.18)  21.466 ms  7.138 ms  6.714 ms
 8  196.24.33.35 (196.24.33.35)  8.092 ms * *
root@pappasfw:/etc/ppp/peers#

```
now ppp1 goes up, and I route 196.43.11.202 through it, arbitrarily for the sake of demonstration, as it was the second hop before
```

root@pappasfw:/etc/ppp/peers# ip route add 196.43.11.202 dev ppp1
root@pappasfw:/etc/ppp/peers# traceroute 196.24.33.35
traceroute to 196.24.33.35 (196.24.33.35), 30 hops max, 60 byte packets
 1  dsl-242-108-01.telkomadsl.co.za (41.242.108.1)  5.842 ms  7.152 ms  7.226 ms
** 2  * * ***
 3  196.43.25.138 (196.43.25.138)  13.169 ms  14.593 ms  15.553 ms
 4  internet-solutions-gw.telkom-ipnet.co.za (196.25.46.90)  17.221 ms  18.239 ms  19.673 ms
 5  168.209.1.170 (168.209.1.170)  51.166 ms 196.26.0.10 (196.26.0.10)  51.356 ms  51.574 ms
 6  * * *
 7  jnb2-vl700-jnb1-vl700.net.tenet.ac.za (155.232.6.18)  13.866 ms  13.241 ms  13.493 ms
 8  196.24.33.35 (196.24.33.35)  12.997 ms * *
root@pappasfw:/etc/ppp/peers#

```
Perhaps if I explicitly specified that the trace should be done from a specific interface, then this behaviour could be expected, but if it's just a general straightforward traceroute <ip> then you'd expect to see all the IP addresses if they are actually reachable at all and they constitute the hops

Also, all computers who use this server as a gateway (including windows machines) also experience this 'firewall effect' since the switch from debian 5 to ubuntu 10.10, so I doubt it's a traceroute-specific problem but rather a routing or kernel configuration?

---

### Post by fragtion on 2010-12-15
Anybody know what could be causing this difference in behaviour? My sysctl settings seem identical, and I'm running both distro's with default firewall settings/scripts, so it's something else that's been modified by devs in that time... xD

---

### Post by fragtion on 2010-12-20
**Update:** I've [posted a more elaborate explanation]("http://www.linuxquestions.org/questions/linux-networking-3/split-routing-traceroute-not-displaying-unrouted-hops-850724/") of this issue on linuxquestions.org, if anyone happens to arrive here with the same problem...

---

### Post by fragtion on 2011-01-21
If anyone else stumbles upon this little pest, I found the solution (for my case at least)!:

rp_filter must be disabled for the relevant interfaces

echo "0" > /proc/sys/net/ipv4/conf/all/rp_filter

edit /etc/sysctl.conf:
> 
# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=0
net.ipv4.conf.all.rp_filter=0

and then reboot

---

