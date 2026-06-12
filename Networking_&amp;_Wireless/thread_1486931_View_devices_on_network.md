---
title: "View devices on network"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Flyboy712 on 2010-05-18
Ok dumb question...probably something as simple as hey open your eyes....haha:

Just wondering if there is a way to view all connected devices on my network??  Something similar to view network map in vista??  I know the places network but that only shows me my shares and I want to be able to see everything that is on there ie  printers, routers, VOIP, other non-shared computers, etc... 

Thanks,
Mike

---

### Post by cariboo on 2010-05-18
I use:

```
sudo nmap -sP 192.168.9.0/24
```

which gives me a list that looks like this:

```
sudo nmap -sP 192.168.1.0/24

Starting Nmap 5.00 ( http://nmap.org ) at 2010-05-18 13:58 PDT
Host 192.168.1.1 is up (0.00069s latency).
MAC Address: 00:25:9C:4D:52:0A (Cisco-Linksys)
Host 192.168.1.2 is up (0.00089s latency).
MAC Address: 00:40:10:20:00:01 (Sonic Systems)
Host 192.168.1.103 is up (0.00014s latency).
MAC Address: 00:14:2A:EF:C2:18 (Elitegroup Computer System Co.)
Host 192.168.1.215 is up.
Host alexis (192.168.1.225) is up (0.000084s latency).
MAC Address: 00:24:21:B7:69:49 (Micro-star Int'l CO.)
Host 192.168.1.230 is up (0.00061s latency).
MAC Address: 00:80:77:89:A3:29 (Brother Industries)
Host puntzi (192.168.1.235) is up (0.000073s latency).
MAC Address: 00:30:65:44:F6:94 (Apple Computer)
Host willy (192.168.1.250) is up (0.000056s latency).
MAC Address: 40:61:86:62:EB:B9 (Unknown)
Nmap done: 256 IP addresses (8 hosts up) scanned in 2.67 seconds
```

I haven't found anything that will do it graphically like windows 7

Edit I did find a utility called lanmap, it is in the jaunty repositories, it outputs a picture, see attachment:

---

### Post by Flyboy712 on 2010-05-19
Thanks I knew it was something simple.

Mike

---

### Post by Aa_Lok on 2010-05-20
It doesn't work for me.

---

### Post by danickstr on 2012-11-19
i guess it requires the nmap.org download  12.04 does not recognize it.

edit: I just tried apt-get install nmap and was denied for not being root

---

### Post by wildmanne39 on 2012-11-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

