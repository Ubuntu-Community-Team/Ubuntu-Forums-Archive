---
title: "Failing to download some websites"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by Peter Bell on 2012-03-20
I'm not sure whether this is an ubuntu problem, or not.

Some websites, while I can connect, don't serve any content (eg [www.skype.com](www.skype.com) and [www.ubuntu.com](www.ubuntu.com)).  Most websites work perfectly well (eg [www.bbc.co.uk](www.bbc.co.uk)).  This doesn't seem to be browser related, since wget is failing.

ping and ICMP traceroute works perfectly well.

I've contacted my ISP, and they tell me that they do not block any websites (although I do know that they block port 25 traffic).

I'm at a loss to know where to go from here - can anyone help me?  Some terminal output from my feeble attempts to find the problem:

```
peter@desktop:~$ wget www.ubuntu.com
--2012-03-21 10:38:45--  http://www.ubuntu.com/
Resolving www.ubuntu.com... 91.189.89.88
Connecting to www.ubuntu.com|91.189.89.88|:80... ^C
peter@desktop:~$ wget www.bbc.co.uk
--2012-03-21 10:39:21--  http://www.bbc.co.uk/
Resolving www.bbc.co.uk... 212.58.244.70
Connecting to www.bbc.co.uk|212.58.244.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 112489 (110K) [text/html]
Saving to: `index.html'

100%[======================================>] 112,489     54.5K/s   in 2.0s    

2012-03-21 10:39:25 (54.5 KB/s) - `index.html' saved [112489/112489]

peter@desktop:~$ sudo traceroute -I www.ubuntu.com
traceroute to www.ubuntu.com (91.189.90.41), 30 hops max, 60 byte packets
 1  10.2.0.2 (10.2.0.2)  0.689 ms  0.845 ms *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * 120.28.0.54 (120.28.0.54)  182.204 ms  182.272 ms
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * ae-6-6.ebr1.Chicago1.Level3.net (4.69.140.189)  246.309 ms
12  ae-2-2.ebr2.NewYork2.Level3.net (4.69.132.66)  261.973 ms  262.891 ms  264.113 ms
13  ae-1-100.ebr1.NewYork2.Level3.net (4.69.135.253)  273.994 ms  274.963 ms  275.458 ms
14  ae-4-4.ebr1.NewYork1.Level3.net (4.69.141.17)  402.889 ms  405.099 ms  406.297 ms
15  ae-44-44.ebr2.London1.Level3.net (4.69.137.77)  337.086 ms  338.258 ms  338.992 ms
16  * * *
17  ae-3-3.ebr2.London2.Level3.net (4.69.141.190)  337.222 ms  346.976 ms  347.160 ms
18  ae-2-54.edge4.London2.Level3.net (4.68.117.116)  457.138 ms  455.045 ms  456.226 ms
19  DATAHOP-LTD.edge4.London2.Level3.net (212.187.192.178)  328.732 ms  329.928 ms  331.101 ms
20  * * *
21  jujube.canonical.com (91.189.90.41)  325.618 ms  326.126 ms  327.829 ms
peter@desktop:~$
```

---

### Post by Peter Bell on 2012-03-21
Strange!  [www.ubuntu.com](www.ubuntu.com) has now started working - but I note that it's now using a different ip.  Earlier, wget [www.ubuntu.com](www.ubuntu.com) was connecting to 91.189.89.88, now it's connecting to 91.189.90.40.

However, I'm still getting a failure to connect to [www.skype.com](www.skype.com)

Can anyone suggest what I can do to investigate further?

---

### Post by noobgirl on 2012-03-21
I would suggest you try a new dns.  8.8.8.8 is the google one or 8.8.4.4
 
> **Peter Bell said:**
> Strange! [www.ubuntu.com]("http://www.ubuntu.com") has now started working - but I note that it's now using a different ip. Earlier, wget [www.ubuntu.com]("http://www.ubuntu.com") was connecting to 91.189.89.88, now it's connecting to 91.189.90.40.
 
However, I'm still getting a failure to connect to [www.skype.com]("http://www.skype.com")
 
Can anyone suggest what I can do to investigate further?

---

### Post by Peter Bell on 2012-03-22
I had already tried using alternative DNS servers, but this doesn't resolve the problem.

Skype started working yesterday, but is now failing again.

[www.seagate.com](www.seagate.com) is also failing this morning.

---

### Post by jonobr on 2012-03-23
I would run a tcpdump

```
sudo tcpdump -nnvXSs 1600 -i any port 80 
```

then go to the problematic website.

Post results back here if your comfortable with doing so.


Are you using some proxy or have you being using ufw or iptables?

---

### Post by ranger1021994 on 2012-03-23
There maybe a problem with website or browser...many times browsers dont work in best condition...
If u want to access just simple text websites..U can try command line browser called LYNX (Its there for Lucid idk about others)...
:) :)

---

### Post by jonobr on 2012-03-23
Hi There


I would normally agree and its a good test, however, OP used wget so im not sure thats the issue.
I could be wrong though!!

---

