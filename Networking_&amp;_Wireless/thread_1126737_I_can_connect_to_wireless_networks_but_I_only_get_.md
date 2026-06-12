---
title: "I can connect to wireless networks but I only get data tranfers on my home wireless."
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Maxepr on 2009-04-15
I use Ubuntu 8.10. When I connect to my home wireless network, everthing is fine. When I connect to other networks....public, private...etc, it shows that I am connected an that everything is fine but I get no data transfer. None of the available browsers will display anything and the email programs don't either. They just keep telling me that there is no connection but the computer says I am connected. 

I can even ping the servers so I MUST be connected but I get nothing else. Why would my own wireless work normally but all the others won't?

I would appreciate any ideas.
Thx,
Steve

---

### Post by Crafty Kisses on 2009-04-15
What are the results of the following?
```
route -n
```
Have you also tried pinging your ISP?

---

### Post by Maxepr on 2009-04-16
Here is the terminal display after typing "route -n" from two of the locations. The first display is the one that does NOT work. The second did not work yesterday but DOES work today. I did nothing different. ARG! 

FIRST LOCATION:

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

10.242.118.0    0.0.0.0         255.255.255.0   U     2      0        0 ath0

169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0


SECOND LOCATION:


Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 ath0

169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0

0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0

MAXEPR

---

