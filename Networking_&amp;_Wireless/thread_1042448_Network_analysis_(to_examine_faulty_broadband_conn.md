---
title: "Network analysis (to examine faulty broadband connection) - best software to use?"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by jommoner on 2009-01-17
Hi!

I have a really useless broadband connection. It started off with a minor fault, but every time a fault is reported, they repair it, causing a new fault to appear, and then the old list of faults return over the next 12 hours.

Originally, it had, every 3 minutes or so, a 10-20 second total disconnect (no internet packets to/from ISP).

Now, it has every 2 minutes or so, a 10-20 second disconnect, but it also have disconnects for a few minutes to a few hours, and it also has 30-60% packet loss for those times when it has connected. Just put in the next complaint but don't know how much longer I will be able to access the internet!

I am using the 'ping' command which gives an idea (that is where I get the packet loss figures from). What I would like to do, would be to find a piece of software that can properly test the broadband connection, showing exactly what is the pattern of packet loss, and so on. Is there anything like this on Ubuntu? I have installed Wireshark but it seems that it isn't what I really need!

The end result of a ping command with -w 350 is :
350 packets transmitted, 213 received, 39% packet loss, time 349977ms
rtt min/avg/max/mdev = 11.680/22.498/83.599/7.892 ms

And, the fault isn't with my local network - I am in a rural area with ground-ground satellite transmission - and it did work very well... once...!

Thank you for any help with this :)

---

### Post by ac7ss on 2009-01-17
first run a traceroute to a known good site. (I use microsoft.com)
This should give you several lines like this```
traceroute to microsoft.com (207.46.197.32), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  4.318 ms  4.748 ms *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * pos-0-0-0-0-cr01.seattle.wa.ibone.comcast.net (68.86.85.205)  18.066 ms  21.138 ms
 7  te-3-3.car1.Seattle1.Level3.net (4.79.104.109)  20.602 ms  20.835 ms  21.569 ms
 8  MICROSOFT-C.car1.Seattle1.Level3.net (4.53.144.22)  22.553 ms  23.164 ms  23.398 ms
 9  ge-5-2-0-55.tuk-64cb-1b.ntwk.msn.net (207.46.41.53)  21.746 ms  22.106 ms  22.717 ms
10  ge-7-1-0-0.cpk-64c-1a.ntwk.msn.net (207.46.35.2)  23.951 ms  24.686 ms  24.046 ms
11  ten3-4.cpk-76c-1b.ntwk.msn.net (207.46.34.118)  23.531 ms  24.266 ms  14.892 ms
12  * * *
13  * * *
14  * * *
15  * * *

```
try a constant ping to each of the nodes ```
sudo ping -f address
``` for a few seconds starting with the top address (press Ctrl-c to stop). the one that gets followed by a lot of ...... is the one that is not connecting.
Caution: do not ping -f more than necessary, it floods the target and network between here and there with a LOT of traffic. I did 138 pings in 1.8 seconds.

---

### Post by oygle on 2009-01-17
Go to Synaptic Package Manager and search for 'packet'. I saw a package called 'bing' there

> Bing is a point-to-point bandwidth measurement tool (hence the 'b'),
based on ping.

Bing determines the real (raw, as opposed to available or average)
throughput on a link by measuring ICMP echo requests' round trip times
for different packet sizes at each end of the link.

Website: [http://fgouget.free.fr/bing/bing_src-readme-1st.shtml](http://fgouget.free.fr/bing/bing_src-readme-1st.shtml)

there are no doubt a few of these tools.

---

