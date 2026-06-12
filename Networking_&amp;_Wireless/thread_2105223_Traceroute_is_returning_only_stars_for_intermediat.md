---
title: "Traceroute is returning only stars for intermediate hops."
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by HunterDX77M on 2013-01-15
I'm completely new to networking. In fact, I just started learning today. 

I was trying to use traceroute to see all the different places that a packet goes through before it hits Google.com.
```
traceroute www.google.com
```

However, after the first two hops, I only get stars up until the final hop to Google:
```

traceroute to www.google.com (173.194.75.147), 30 hops max, 60 byte packets
 1  . (192.168.2.1)  0.340 ms  0.316 ms  0.455 ms
 2  dslrouter (192.168.1.1)  2.425 ms  2.410 ms  2.393 ms
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
15  www.google.com (173.194.75.147)  52.674 ms  55.299 ms  58.225 ms

```

I learned that unresponsive router hops and lost probes generate this message so I tried it with ten probes, with a similar result. 

```
traceroute www.google.com -q 10
```
```
traceroute to www.google.com (173.194.75.147), 30 hops max, 60 byte packets
 1  . (192.168.2.1)  0.329 ms  0.305 ms  0.419 ms  0.400 ms  0.561 ms  0.543 ms  0.524 ms  0.508 ms  0.633 ms  0.619 ms
 2  dslrouter (192.168.1.1)  4.250 ms  4.217 ms  4.198 ms  4.348 ms  5.060 ms  5.565 ms  1.972 ms  2.109 ms  3.738 ms  3.734 ms
 3  * * * * * * * * * *
 4  * * * * * * * * * *
 5  * * * * * * * * * *
 6  * * * * * * * * * *
 7  * * * * * * * * * *
 8  * * * * * * * * * *
 9  * * * * * * * * * *
10  * * * * * * * * * *
11  * * * * * * * * * *
12  * * * * * * * * * *
13  * * * * * * * * * *
14  * * * * * * * * * *
15  * * * * * * * * * *
16  * * * * * * * * * *
17  * * * * * * * * * *
18  * * * * * * * * * *
19  * * * * * * * * * *
20  * * * * * * * * * *
21  * * * * * * * * * *
22  * * * * * * * * * *
23  * * * * * * * * * *
24  * * * * * * * * * *
25  * * * * * * * * * *
26  * * * * * * * * * *
27  * * * * * * * * * *
28  * * * * * * * * * *
29  * * * * * * * * * *
30  * * * * * * * * * *

```


**What can I do to see all the information associated with each hop?**

Thanks for any help.

---

### Post by HunterDX77M on 2013-01-17
Bump

---

### Post by SeijiSensei on 2013-01-17
Are you running a firewall?  What are your rules for ICMP traffic?

---

### Post by HunterDX77M on 2013-01-17
> **SeijiSensei said:**
> Are you running a firewall?

Yes. Ubuntu Firewall is on.

> **SeijiSensei said:**
> What are your rules for ICMP traffic?

What does that mean? I've never heard of it before. (n00b)

---

### Post by jonobr on 2013-01-17
Hello


ICMP is a transport layer protocol for sending messages such as errors etc.

ICMP supports ping, so when you ping google.com, the packet goes through several interfaces on routers until it gets to its destination.

What you see in the ping is the sent message and the response.

Now, if the ping doesn't reach the target, it has a feature where if it goes through 16 interfaces (Hops) before it considered the target unreachable and the packet is no longer forwarded.
This stops packets going round a network for ever.

The packet starts with a count of 16 when you start the ping.
Each router reduces the count by 1 to 15, then on the next router to 14 then on the next router to 13 and so, until it goes to 1.

The last router, on receiving a packet with a hop count of 1, and knowing that the end device is not connected to it, sends back an ICMP message to the sender saying , forget about it, target unreachable. It also supplies the end point IP which is considering the packet lost.

Traceroute uses this feature to tell you the route of a packet.
When you issue a traceroute it sends a ping with a count of one,
The next router sends back an unreachable to the sender with its IP.
Then next ping is sent with a count of 2.

The first one (which has already sent the unreachable message in the last packet) now reduces the count from 2 to 1 .
The nect router will then see the 1 and then report back unreachable with the IP.
Another ping is sent with a count of 3 , and so on until the entire route is mapped.
This is where you get the different lines from


Now,for some people they are concerned this provides to much information on the network.

What they do is the dont allow ICMP message responses, so in a typical traceoute you will see devices with stars , who don't want to reveal their IP address.

This is not the case with your trace.
In yours it appears that ICMP messages are not being passed as all of the devices are not showing the ping responses.

SeijiSensei is suggesting , and IM sure rightly, that your firewall is dropping these ICMP messages ,

Every firewall has rules for handling types of packets with different characteristics.
This could be based on IP, traffic type and so on.

EG A ping into your network, could be harmless or could be an attempt to probe your network,
Depending on your firewall type, there may be a GUI saying "allow inbound ICMP request" with a radial button saying yes/no,
or it may be a more command line driven firewall like IPTables or UFW which will mean you need to manually add lines to your config.

You need to look at your router or Ubuntu firewall
to see if there are any rules in there which have a rule for dropping ICMP (ICMP echo request / reply) 

Maybe you clicked an option which is specifically barring this,
again, you will need to figure out what you have and how the thing is configured

---

