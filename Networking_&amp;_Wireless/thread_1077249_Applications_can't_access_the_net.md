---
title: "Applications can't access the net?"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by vinayg18 on 2009-02-22
I'm using a ZTE EVDO USB modem to access the internet via PPP and things are pretty weird. 

Firefox is unable to access the internet, and I realised, by accident, that restarting Firefox fixes the problem. That is to say, every time I want to use Firefox, I need to go to add-ons, enable/disable an add-on to get the Restart Firefox button and after that, things are fine.

The problem's not just with Firefox though. Other applications like Epiphany, Galeon, Pidgin and Empathy also fail to access the internet. 

Pinging, however, is successful.

> vinay@Tudor:~$ ping [www.dlisted.com](www.dlisted.com)
PING [www.dlisted.com](www.dlisted.com) (66.55.145.117) 56(84) bytes of data.
64 bytes from 66.55.145.117.choopa.net (66.55.145.117): icmp_seq=1 ttl=47 time=464 ms
64 bytes from 66.55.145.117.choopa.net (66.55.145.117): icmp_seq=2 ttl=47 time=645 ms
64 bytes from 66.55.145.117.choopa.net (66.55.145.117): icmp_seq=3 ttl=47 time=986 ms
64 bytes from 66.55.145.117.choopa.net (66.55.145.117): icmp_seq=4 ttl=47 time=465 ms


Any idea as to what the problem could be? I'm a new Ubuntu user, so be gentle. :P

Additional Info: I type wvdial in a terminal to access the internet. Gnome PPP works too.

Thank you.

---

### Post by superprash2003 on 2009-02-22
post output of ifconfig from the terminal.. try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220
For reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by vinayg18 on 2009-02-26
Here you go
> vinay@Tudor:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:21:d5:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1080 (1.0 KB)  TX bytes:1080 (1.0 KB)

ppp0      Link encap: Point-to-Point Protocol  
          inet addr:10.3.58.11  P-t-P:192.168.52.12  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2068131 (2.0 MB)  TX bytes:518807 (518.8 KB)



---

### Post by superprash2003 on 2009-02-26
your mtu is fine.. did you try changing DNS servers to opendns

---

