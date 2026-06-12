---
title: "Slow internet connection"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by pepejeria on 2010-12-04
Hi, 

I just installed Ubuntu 10.10 on my Lenovo T400 and I am having problems with slow internet.

I first thought that it could be the wlan drivers, but it is equally slow when connecting it directly to the router with a lan cable.

Any tips on how to proceed with this? Thanks

---

### Post by dineshs on 2010-12-04
Have you tried disabling ipv6?[Here]("http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can") is the procedure
What do you get for```
ping -c3 gmail.com
```pl post results

---

### Post by pepejeria on 2010-12-04
> 
PING gmail.com (74.125.39.17) 56(84) bytes of data.
64 bytes from gmail.com (74.125.39.17): icmp_req=1 ttl=57 time=33.8 ms
64 bytes from gmail.com (74.125.39.17): icmp_req=2 ttl=57 time=35.4 ms
64 bytes from gmail.com (74.125.39.17): icmp_req=3 ttl=57 time=33.7 ms

--- gmail.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 33.749/34.331/35.440/0.812 ms


Disabling IPv6 in Firefox did the trick. Is this something that I need to do as well for other programs connecting to the internet? Such as eclipse?

Thanks you for your answer.

---

### Post by pepejeria on 2010-12-04
Found the following [link]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html") to disable IPv6 system wide, but I am not sure if this is the way to go.

---

