---
title: "&#65279;A baffling  network/usenet problem"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by holadebob on 2010-10-09
I have 512K service from a fixed wireless system here in Panama called Mobilnet IP 200.3.200.5.

I get good “fast” downloads (60Kb/s) when I update Ubuntu or download stuff from torrent sources, websites, etc. 

I decided to go to usenet for some nzb downloads and then downloaded and installed Sabnzbd+ and also Pan. I signed up with Astraweb and later, because I was having this problem, signed up with Newshosting to help determine if the problem was with usenet servers.  I now have two usenet server subscriptions with the same problem.

The problem is that I almost always get only 5 to 6Kb/s downloads from them, for many different files, different times of the day. I should be getting 60Kb/s from a good server (like Ubuntu's, or most web pages, Google, etc.) 

I've contacted the tech services for these sites and have gone through their lists of things to do, changing ports, connections, servers, etc, to no avail. One guy from Astraweb told me I have a problem in the network somewhere or on my computer system. 

Can someone out there that can decipher all this stuff tell me what the heck or who the heck is restricting my usenet downloads, is it Ubuntu or my configuration with Ubuntu. There's no firewall to my knowledge, but seem to have heard there is one but it doesn't stop anything. Dunno.

Here is some info:

$ ping -c 5 news.astraweb.com
PING news.astraweb.com (207.246.207.167) 56(84) bytes of data.
64 bytes from 167.sjc.astraweb.com (207.246.207.167): icmp_seq=1 ttl=54 time=191 ms
64 bytes from 167.sjc.astraweb.com (207.246.207.167): icmp_seq=2 ttl=54 time=186 ms
64 bytes from 167.sjc.astraweb.com (207.246.207.167): icmp_seq=3 ttl=54 time=180 ms
64 bytes from 167.sjc.astraweb.com (207.246.207.167): icmp_seq=4 ttl=54 time=191 ms
64 bytes from 167.sjc.astraweb.com (207.246.207.167): icmp_seq=5 ttl=54 time=185 ms

--- news.astraweb.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 180.467/187.032/191.906/4.292 ms
clark@office:~$ ping -c 5 news.newshosting.com
PING news.iad.newshosting.com (209.197.12.12) 56(84) bytes of data.
64 bytes from news.iad.newshosting.com (209.197.12.12): icmp_seq=1 ttl=54 time=137 ms
64 bytes from news.iad.newshosting.com (209.197.12.12): icmp_seq=2 ttl=54 time=128 ms
64 bytes from news.iad.newshosting.com (209.197.12.12): icmp_seq=3 ttl=54 time=137 ms
64 bytes from news.iad.newshosting.com (209.197.12.12): icmp_seq=4 ttl=54 time=123 ms
64 bytes from news.iad.newshosting.com (209.197.12.12): icmp_seq=5 ttl=54 time=123 ms

--- news.iad.newshosting.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 123.028/130.148/137.782/6.327 ms
clark@office:~$ 


traceroute news.astraweb.com
traceroute to news.astraweb.com (216.151.153.166), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
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
clark@office:~$ 
 

I get the same results with news.newshosting.com

Sometimes I'll get some info where some of the asterisks are replaced by stuff, but it is intermittant.

And here's ifconfig which I don't understand, like most things here.

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:c4:0d:77  
          inet addr:190.2.227.131  Bcast:190.2.227.191  Mask:255.255.255.192
          inet6 addr: fe80::21d:7dff:fec4:d77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91373537 (91.3 MB)  TX bytes:4830402 (4.8 MB)
          Interrupt:26 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:416487 (416.4 KB)  TX bytes:416487 (416.4 KB)

Hoping that I haven't overwhelmed you with my ignorance, please let me know if anything pops out at you and what might be causing this crazy problem. My ISP claims they do not filter my stuff, but is there a way to test that?

Thank you for reading  - Bob

---

