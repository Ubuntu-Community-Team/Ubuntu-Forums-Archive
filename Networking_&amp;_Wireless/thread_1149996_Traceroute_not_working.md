---
title: "Traceroute not working"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by Kismet on 2009-05-05
```
$ traceroute www.google.com
traceroute to www.google.com (74.125.155.103), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *^C
$ traceroute6 www.google.com
traceroute: unknown host www.google.com
$ ping www.google.com
PING www.l.google.com (74.125.155.99) 56(84) bytes of data.
64 bytes from px-in-f99.google.com (74.125.155.99): icmp_seq=1 ttl=243 time=36.1 ms
64 bytes from px-in-f99.google.com (74.125.155.99): icmp_seq=2 ttl=243 time=69.5 ms
64 bytes from px-in-f99.google.com (74.125.155.99): icmp_seq=3 ttl=243 time=36.5 ms
^C
```

What am I doing wrong? 
traceroute6 didn't work, thought it might be an ipv6 issue. I installed the regular old traceroute, still doesn't work. Of course I can connect to sites fine, ssh, etc.

---

### Post by forgewire on 2009-09-08
Absolutely the same problem on Jaunty.
traceroute to [www.google.com](www.google.com) (66.102.9.147), 6 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *

What's wrong here?

---

### Post by cak3 on 2009-09-08
Huh. Seems to work fine for me. You behind some sort of crazy firewall? Maybe try "sudo tracert google.com"

---

### Post by zlawhorn on 2009-09-28
I'm getting the same problem.


zach@zach-laptop:~$ sudo traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (208.67.216.230), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *^C
zach@zach-laptop:~$ ping [www.google.com](www.google.com)
PING google.navigation.opendns.com (208.67.216.230) 56(84) bytes of data.
64 bytes from 208.67.216.230: icmp_seq=1 ttl=55 time=15.1 ms
^C64 bytes from 208.67.216.230: icmp_seq=2 ttl=55 time=15.8 ms

--- google.navigation.opendns.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 5038ms
rtt min/avg/max/mdev = 15.196/15.534/15.873/0.360 ms

---

### Post by unutbu on 2009-09-28
I don't think there is anything wrong; it's just that some sites block traceroute requests: 

From [http://en.wikipedia.org/wiki/Traceroute:](http://en.wikipedia.org/wiki/Traceroute:)

> For these reasons, while traceroute was widely unrestricted during the early days of the Internet, today many networks block traceroute requests, or de-prioritize the ICMP time exceeded message that is required to determine round trip time. However, filtering traffic except at network end-points is a controversial practice.

An alternate method which gives traceroute-type infomation, albeit in a different form, is:
```
dig google.com +trace

```

---

### Post by zlawhorn on 2009-09-28
Yes it is true that some block ICMP traffic but they do not block it in the sense  that they don't allow it to go through. What happens is that it will allow the traceroute to go through but will not send any information back, only astrix. But this will only happen on the one address that is blocking ICMP traffic, you will still be able to see the other hops as the traceroute goes from place to place. I also tried a trouceroute on the IP adress 4.2.2.2 which is an IP that i know I can traceroute because I am doing it from the Windows machine next to me. I have also tried on numerous adresses and names and I get the same results so something is going on. 


As for the dig command im not sure what i should be seeing but this is what happens:

[I]zach@zach-laptop:~$ dig [www.google.com](www.google.com) +trace

; <<>> DiG 9.5.1-P2 <<>> [www.google.com](www.google.com) +trace
;; global options:  printcmd
;; Received 17 bytes from 208.67.222.222#53(208.67.222.222) in 13 ms

zach@zach-laptop:~$ [/I]

I was hoping for a list of all the hops that my packet takes to get to the specified address.  Thank you for your time.

---

### Post by iiiears on 2011-05-13
sudo traceroute -I

---

### Post by abedayyad on 2011-07-23
Greetings. 

I'm having a problem similar to the above, so I hope nobody minds if I re-invigorate this post. 

When I try do something similar, I get: 


> /$ traceroute6 google.com 
traceroute: unknown host google.com

dig + trace works, as does ping. I am wondering if this is something to do with my DNS server and how it is set up? I can not seem to find an IP address other than the one which only makes sense within my wifi network: 192.168.... 

Do I have the right idea, or am I just completely wrong?

---

### Post by El Gabito on 2011-09-09
> **iiiears said:**
> sudo traceroute -I

You are awesome. This works. Should be top hit on Google (it's not).

---

### Post by Fracta on 2012-04-16
The -I switch doesn't work for me, here are my results:

traceroute to [www.google.com](www.google.com) (74.125.237.52), 30 hops max, 60 byte packets
 1  * * *
 etc, etc, more stars
16  * * *
17  syd01s05-in-f20.1e100.net (74.125.237.52)  457.687 ms  458.293 ms  458.917 ms

The only difference the -I switch made was the packet would actually get there. If I don't use it, i just get * * * forever.

I know why the switch works, but I don't know why I'm not getting any information from the hops. I could do it in windows easy enough with tracert. Why isn't linux working? I have tried mtr and tracepath as well, and none work.

---

### Post by nothingspecial on 2012-04-16
Please do not bump old threads to the top.

Also, one thread per question please.

Closed.

---

