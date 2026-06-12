---
title: "Periodically high ping with Broadcom wireless card"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by cckerr on 2012-02-08
I know I'm not the only one having problems with Broadcom wireless cards and Ubuntu, but I've scoured the forum and haven't found anyone with this particular issue.

The problem is that periodically (about every 10 seconds), the ping to my router goes from 2-3 ms to 100-200 ms:

josquin:~> ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=2.86 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=2.87 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=2.84 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=2.77 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=141 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=132 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=98.8 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=66.6 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=44.7 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=42.9 ms
64 bytes from 192.168.0.1: icmp_seq=11 ttl=64 time=11.4 ms
64 bytes from 192.168.0.1: icmp_seq=12 ttl=64 time=2.79 ms
64 bytes from 192.168.0.1: icmp_seq=13 ttl=64 time=2.81 ms
64 bytes from 192.168.0.1: icmp_seq=14 ttl=64 time=2.83 ms
64 bytes from 192.168.0.1: icmp_seq=15 ttl=64 time=2.81 ms
64 bytes from 192.168.0.1: icmp_seq=16 ttl=64 time=2.84 ms
64 bytes from 192.168.0.1: icmp_seq=17 ttl=64 time=140 ms
64 bytes from 192.168.0.1: icmp_seq=18 ttl=64 time=120 ms
64 bytes from 192.168.0.1: icmp_seq=19 ttl=64 time=98.8 ms
64 bytes from 192.168.0.1: icmp_seq=20 ttl=64 time=67.8 ms
64 bytes from 192.168.0.1: icmp_seq=21 ttl=64 time=66.8 ms
64 bytes from 192.168.0.1: icmp_seq=22 ttl=64 time=25.0 ms
64 bytes from 192.168.0.1: icmp_seq=23 ttl=64 time=3.63 ms
64 bytes from 192.168.0.1: icmp_seq=24 ttl=64 time=2.83 ms
64 bytes from 192.168.0.1: icmp_seq=25 ttl=64 time=2.76 ms

The ping latency problem is almost perfectly periodic; here's a graph of 120 consecutive pings:
[http://www.cingulate.net/ping-problem.png](http://www.cingulate.net/ping-problem.png)

I have Ubuntu 10.04 64 bit on a Dell Studio 1557, the wireless card is a Broadcom 4353, the router is a Netgear DG834G.

Things I've tried are:
* Using Ethernet instead; problem disappears (pings consistently <1 ms), so it's definitely the wireless connection;
* Using the wireless card via Windows 7 on the same computer; problem disappears, so there's nothing *intrinsically* wrong with the wireless card or router;
* Turning off power management (sudo iwconfig wlan0 power off); problem remains, so it's not a power issue;
* Downloading and installing the latest Linux Broadcom driver ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)); problem remains;
* Checking to see if there's any extra network traffic or extra netstat connections during the slow ping periods; there isn't, so it isn't a traffic congestion issue;
* Removing DNS servers to stop all TCP connections; problem remains, so it definitely isn't a traffic issue
* Using a clean user account with no software installed; problem remains, so it's a default/root problem
* Trying a reverse ping (router -> computer); problem remains

I'm at my wit's end, so if anyone has any suggestions, I'd be extremely grateful!

---

