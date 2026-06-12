---
title: "Can't connect to web server"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by nodiesop1 on 2009-12-12
This post is not Ubuntu related, but I thought I'd drop it in here to see if anyone with networking knowledge can explain to me what is going on...

I cannot access the server cl68.justhost.com (or more importantly any website I have hosted there).  I can access [www.justhost.com](www.justhost.com).

Justhost support said it's a problem with my ISP.  I contacted them (surewest comm) and they said there was no problem on their end.  A friend who uses the same ISP can connect to the cl68 server no problem.  From any other ISP I can connect fine--so it only seems to be something with my local network.

Here's what tracepath says for cl68.justhost.com:

 1:  ubuntu.local (10.202.46.2)                            0.122ms pmtu 1500
 1:  10.202.46.1 (10.202.46.1)                              1.170ms 
 1:  10.202.46.1 (10.202.46.1)                              1.099ms 
 2:  fe000.nrp-c2-b4.net.surewest.net (66.60.13.64)      101.513ms 
 3:  66.60.130.81 (66.60.130.81)                           97.116ms 
 4:  233.153-60-66-biz-static.surewest.net (66.60.153.233)  99.213ms 
 5:  66.60.130.206 (66.60.130.206)                        104.468ms asymm  4 
 6:  250.152-60-66-biz-static.surewest.net (66.60.152.250) 104.589ms asymm  5 
 7:  te-4-1.car1.Sacramento1.Level3.net (4.53.200.9)       96.612ms asymm  6 
 8:  ae-11-11.car2.Sacramento1.Level3.net (4.69.132.150)   96.930ms asymm  7 
 9:  ae-4-4.ebr2.SanJose1.Level3.net (4.69.132.158)       117.003ms asymm  8 
10:  ae-3.ebr1.Denver1.Level3.net (4.69.132.58)           131.637ms asymm  9 
11:  ae-1-100.ebr2.Denver1.Level3.net (4.69.132.38)       125.063ms asymm 10 
12:  ae-3.ebr1.Chicago2.Level3.net (4.69.132.62)          148.188ms asymm 11 
13:  ae-6.ebr1.Chicago1.Level3.net (4.69.140.189)         151.253ms asymm 12 
14:  ae-13-51.car3.Chicago1.Level3.net (4.68.101.7)       151.506ms asymm 13 
15:  xe-0-3-0.cr2.ord1.us.nlayer.net (4.71.101.14)        147.253ms asymm 12 
16:  no reply
.
.
.
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 

Anybody have any idea why I can't connect to this one server?

Thanks.

---

### Post by Mski35 on 2009-12-12
I was able to traceroute both addresses however cl68.justhost.com took 14 hops and resolved to the following:

14  cl68.justhost.com (69.175.66.58)  55.284 ms  58.260 ms  59.100 ms

My traceroute to [www.justhost.com](www.justhost.com) took 11 hops and resolved to the following:

11  67.225.149.185 (67.225.149.185)  75.451 ms  76.107 ms  47.179 ms

I tried accessing cl68.justhost.com from a browser as well as the resolved IP address but I receive a message "Website not Found".   

I would check and make sure there is a route added to the address and more importantly I would lean on justhost.com to determine why your subdomain cl68 isn't available to anyone not on the same network.

---

### Post by zaphod777 on 2009-12-12
> **Mski35 said:**
> I was able to traceroute both addresses however cl68.justhost.com took 14 hops and resolved to the following:

14  cl68.justhost.com (69.175.66.58)  55.284 ms  58.260 ms  59.100 ms

My traceroute to [www.justhost.com](www.justhost.com) took 11 hops and resolved to the following:

11  67.225.149.185 (67.225.149.185)  75.451 ms  76.107 ms  47.179 ms

I tried accessing cl68.justhost.com from a browser as well as the resolved IP address but I receive a message "Website not Found".   

I would check and make sure there is a route added to the address and more importantly I would lean on justhost.com to determine why your subdomain cl68 isn't available to anyone not on the same network.

Yes seams to be some routing problems make sure you keep pushing till you get someone who knows CISCO. A lower level help desk person may try and blow you off saying its not their problem when it clearly is.

---

