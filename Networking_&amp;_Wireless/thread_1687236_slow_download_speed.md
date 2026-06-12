---
title: "slow download speed"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by wightolore on 2011-02-13
Windows laptop: [http://img716.imageshack.us/img716/7240/sisterslaptop.png](http://img716.imageshack.us/img716/7240/sisterslaptop.png)
Ubuntu desktop: [http://img52.imageshack.us/img52/189/screenshot1uu.png](http://img52.imageshack.us/img52/189/screenshot1uu.png)

both using wireless and both right next to each other.
the ubuntu distro wasn't always this bad, but just recently its started to get alot slower.. and right now its almost unbearable
game pings are so high (4000-16000ms!) and downloads have dropped to less than 20 Kb/s

any other information i can give please let me know

---

### Post by wightolore on 2011-02-13
oh and here's a traceroute to google.com

weebz@weebzlinux:~$ traceroute google.com
traceroute to google.com (72.14.204.99), 30 hops max, 60 byte packets
 1  10.53.192.1 (10.53.192.1)  261.248 ms  262.339 ms  263.067 ms
 2  gig3-11.akrnoh2-swt401.neo.rr.com (24.164.118.9)  268.803 ms  270.530 ms  271.640 ms
 3  tge5-0-0.ncntoh1-rtr1.neo.rr.com (24.164.102.170)  274.368 ms  275.225 ms  276.329 ms
 4  tge1-0-1.clboh1-rtr0.mwrtn.rr.com (65.25.137.193)  277.437 ms  280.167 ms  282.650 ms
 5  ae-4-0.cr0.chi30.tbone.rr.com (66.109.6.68)  291.007 ms  293.236 ms  296.714 ms
 6  ae-1-0.pr0.chi10.tbone.rr.com (66.109.6.155)  297.682 ms  45.336 ms  202.256 ms
 7  74.125.48.109 (74.125.48.109)  202.730 ms  203.084 ms  203.937 ms
 8  72.14.236.178 (72.14.236.178)  242.539 ms  212.398 ms  243.622 ms
 9  209.85.248.222 (209.85.248.222)  209.367 ms  212.974 ms  215.574 ms
10  66.249.94.46 (66.249.94.46)  248.175 ms 66.249.94.54 (66.249.94.54)  245.410 ms 66.249.94.46 (66.249.94.46)  248.890 ms
11  iad04s01-in-f99.1e100.net (72.14.204.99)  63.802 ms * *

my windows comp is easily below 100 and right around 50

---

### Post by sikander3786 on 2011-02-13
Welcome to the forums :-)

Try disabling IPv6. It is known to cause problems like slow browsing and slow downloads.

The server for webupd8 is not responding. You can view a cached copy here.

[http://webcache.googleusercontent.com/search?q=cache:ADlkng9FgtMJ:www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html+disable+ipv6+ubuntu&cd=1&hl=en&ct=clnk&source=www.google.com](http://webcache.googleusercontent.com/search?q=cache:ADlkng9FgtMJ:www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html+disable+ipv6+ubuntu&cd=1&hl=en&ct=clnk&source=www.google.com)

Or, see this one.

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by wightolore on 2011-02-13
Thanks for the fast response.
Unfortunately after disabling ipv6 it seemed to work for a little while, but now the internet is not even usable. It says it is connect and I have an IP from my modem/router (SBG900) .. and I can access pages VERY VERY VERY slowly it is utterly impossible to be anywhere near productive. 

Its weird because my Windows laptop sitting right next to this linux computer is traceroute'ing to [www.google.com](www.google.com) with less than 100 ms on each hop while my linux computer is >250ms even on the first hop to my 'local' RR network (10.x.x.x).

There has got to be a way to diagnose this that I'm unfamiliar with.

---

