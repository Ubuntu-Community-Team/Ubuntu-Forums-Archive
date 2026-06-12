---
title: "Broadcom STA 43 wireless slow after update"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by dnr1128 on 2011-09-22
Last night I did a normal system update, and with the security updates came an update for my wireless, the infamous Broadcom 43x.  Now, it still works, but it is very slow on connecting to the router, and connecting to websites.  I'm running 11.04 on a Lenovo IdeaPad z565.  Prior to this update it worked fine.  Is there a way i can go backwards and remove this latest driver update?

---

### Post by chili555 on 2011-09-22
> the infamous Broadcom 43**x**The specifics about your Broadcom are important. What's under that x? Is it a 4311? 4313 or 4328 or ...?? Please run and post:```
lspci -nn | grep 0280
```

---

### Post by dnr1128 on 2011-09-22
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

In Firefox, it takes five or ten seconds saying "connected to (website)".  I am using OpenDNS in the IPv4 settings, and its always worked well.  I'm on a satellite connection, with ping times running around 600ms.  It seems that after I've been on a site for a minute or two it'll start loading that site faster.

---

### Post by chili555 on 2011-09-22
Let's see what driver is being used and if there are any interesting kernel messages:```
lsmod | grep -e b43 -e ssb -e wl
dmesg | grep -e b43 -e ssb -e wl
```Also let us see:```
ping -c3 72.14.204.103
ping -c3 www.google.com
```Thanks.

---

### Post by dnr1128 on 2011-09-22
> **chili555 said:**
> Let's see what driver is being used and if there are any interesting kernel messages:```
lsmod | grep -e b43 -e ssb -e wl
dmesg | grep -e b43 -e ssb -e wl
```Also let us see:```
ping -c3 72.14.204.103
ping -c3 www.google.com
```Thanks.

david@david-IdeaPad-Z565:~$ lsmod | grep -e b43 -e ssb -e wl
wl                   2642531  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
david@david-IdeaPad-Z565:~$ dmesg | grep -e b43 -e ssb -e wl
[    7.841318] wl: module license 'MIXED/Proprietary' taints kernel.
[    7.847962] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.847970] wl 0000:02:00.0: setting latency timer to 64
david@david-IdeaPad-Z565:~$ 


PING 72.14.204.103 (72.14.204.103) 56(84) bytes of data.
64 bytes from 72.14.204.103: icmp_req=1 ttl=48 time=654 ms
64 bytes from 72.14.204.103: icmp_req=2 ttl=48 time=805 ms
64 bytes from 72.14.204.103: icmp_req=3 ttl=48 time=632 ms

--- 72.14.204.103 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 632.785/697.522/805.099/76.591 ms




I looked at the resolv.conf file to make sure that the DNS server was correct, and it was.  It seems to be working a little faster, but I didn't do anything.  Hmm..

---

### Post by chili555 on 2011-09-22
> PING 72.14.204.103 (72.14.204.103) 56(84) bytes of data.
64 bytes from 72.14.204.103: icmp_req=1 ttl=48 time=654 ms
64 bytes from 72.14.204.103: icmp_req=2 ttl=48 time=805 ms
64 bytes from 72.14.204.103: icmp_req=3 ttl=48 time=632 ms

--- 72.14.204.103 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 632.785/697.522/805.099/76.591 msWhat about?```
ping -c3 www.google.com
```The ping by number won't use the DNS nameservers so the times reflect the satellite lag only.

The driver *wl* appears to be the only driver in place and is correct.

---

### Post by dnr1128 on 2011-09-22
PING [www.l.google.com](www.l.google.com) (74.125.67.99) 56(84) bytes of data.
64 bytes from gw-in-f99.1e100.net (74.125.67.99): icmp_req=1 ttl=50 time=799 ms
64 bytes from gw-in-f99.1e100.net (74.125.67.99): icmp_req=2 ttl=50 time=751 ms
64 bytes from gw-in-f99.1e100.net (74.125.67.99): icmp_req=3 ttl=50 time=786 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2929ms
rtt min/avg/max/mdev = 751.069/779.091/799.350/20.486 ms

could it be that the delays is on the server side and not local?

---

### Post by chili555 on 2011-09-22
The ping times with and without DNS are not remarkably different. It looks like satellite lag to me. To which server are you referring? Does this tell us anything useful?```
traceroute www.google.com
```

---

### Post by dnr1128 on 2011-09-23
> **chili555 said:**
> The ping times with and without DNS are not remarkably different. It looks like satellite lag to me. To which server are you referring? Does this tell us anything useful?```
traceroute www.google.com
```

traceroute to [www.google.com](www.google.com) (74.125.67.103), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.749 ms  4.817 ms  5.211 ms
 2  64.19.247.153 (64.19.247.153)  12.642 ms  12.871 ms  13.128 ms
 3  64.19.249.149 (64.19.249.149)  632.691 ms  633.009 ms  633.280 ms
 4  64.19.249.145 (64.19.249.145)  633.724 ms  633.985 ms  799.348 ms
 5  CAPROCK-COM.car1.Houston1.Level3.net (4.78.9.166)  799.600 ms  877.307 ms  877.508 ms
 6  ge-7-3.car1.Houston1.Level3.net (4.78.9.165)  892.305 ms  558.542 ms  599.866 ms
 7  ae-2-5.bar1.Houston1.Level3.net (4.69.132.230)  600.072 ms  600.344 ms  600.808 ms
 8  ae-13-13.ebr1.Dallas1.Level3.net (4.69.137.138)  699.709 ms  699.917 ms  700.169 ms
 9  ae-91-91.csw4.Dallas1.Level3.net (4.69.151.161)  700.418 ms ae-81-81.csw3.Dallas1.Level3.net (4.69.151.149)  700.708 ms ae-71-71.csw2.Dallas1.Level3.net (4.69.151.137)  804.345 ms
10  * * *
11  GOOGLE-INC.edge2.Dallas3.Level3.net (4.59.36.14)  803.405 ms  803.615 ms  803.831 ms
12  72.14.233.65 (72.14.233.65)  599.448 ms  642.307 ms  584.611 ms
13  72.14.237.221 (72.14.237.221)  749.604 ms  853.596 ms 72.14.237.219 (72.14.237.219)  853.793 ms
14  * * *
15  66.249.94.23 (66.249.94.23)  954.816 ms 66.249.94.21 (66.249.94.21)  954.996 ms  1004.605 ms
16  209.85.254.247 (209.85.254.247)  1004.814 ms 72.14.239.131 (72.14.239.131)  1005.179 ms 72.14.239.127 (72.14.239.127)  1005.335 ms
17  209.85.255.190 (209.85.255.190)  589.753 ms  597.620 ms *
18  gw-in-f103.1e100.net (74.125.67.103)  796.300 ms  695.265 ms  695.430 ms

---

### Post by chili555 on 2011-09-23
I think you have to look elsewhere than your computer and router. The request gets to your router from you computer in 5 ms:> 1 [COLOR="Red"]192.168.1.1[/COLOR] (192.168.1.1) 1.749 ms 4.817 ms [COLOR="Red"]5.211 ms[/COLOR]From your router to your internet service provider in 13 ms:> 2 [COLOR="Red"]64.19.247.153[/COLOR] (64.19.247.153) 12.642 ms 12.871 ms [COLOR="Red"]13.128 ms[/COLOR]Thereafter, it's outside your home, I believe.

Unless there is something I'm not seeing (always a possibility), I don't believe you have a driver or other problem on your end.

For comparison, I consider my system to be operating correctly; here are my comparison numbers:> chili@LAPTOP60:~$ traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (72.14.204.147), 30 hops max, 60 byte packets
 1  [COLOR="Red"]192.168.1.254[/COLOR] (192.168.1.254)  13.378 ms  13.546 ms  [COLOR="Red"]13.797 ms[/COLOR]
 2  [COLOR="Red"]adsl-74-235-180-1.clt.bellsouth.net[/COLOR] (74.235.180.1)  50.946 ms  52.953 ms  [COLOR="Red"]53.866 ms[/COLOR]
 3  70.159.208.37 (70.159.208.37)  54.099 ms  54.301 ms  54.790 ms
 4  12.81.34.62 (12.81.34.62)  56.047 ms  59.932 ms  109.382 ms
<snip>

---

### Post by dnr1128 on 2011-09-23
> **chili555 said:**
> I think you have to look elsewhere than your computer and router. The request gets to your router from you computer in 5 ms:From your router to your internet service provider in 13 ms:Thereafter, it's outside your home, I believe.

Unless there is something I'm not seeing (always a possibility), I don't believe you have a driver or other problem on your end.

For comparison, I consider my system to be operating correctly; here are my comparison numbers:

Looking that way.  Thank you for your help!!!

---

