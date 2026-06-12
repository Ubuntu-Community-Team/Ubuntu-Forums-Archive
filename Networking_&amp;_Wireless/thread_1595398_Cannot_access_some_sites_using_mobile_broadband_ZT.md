---
title: "Cannot access some sites using mobile broadband ZTE MF627, Ubuntu 10.10"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by zyperbyte on 2010-10-13
Hi guys, I need help. I'm using a mobile broadband  (PLDT Weroam).

I can access some sites perfectly like gmail and facebook. 

But some sites does not load (ex. [http://addons.mozilla.org](http://addons.mozilla.org)) and some sites do not finish loading (i.e. progress bar does not finish ex. [http://www.bgn.org](http://www.bgn.org)).

I previously had huawei e220, of which I got the same experience that is why I had it replace with the ZTE MF627. Same problem exists so not a hardware issue.

Please help.

---

### Post by hecatae on 2010-10-13
do you have the same problem trying to load [https://addons.mozilla.org/](https://addons.mozilla.org/) 

I own a ZTE MF626, and some mobile broadband providers restrict certain sites due to age restrictions on the sim card.

---

### Post by zyperbyte on 2010-10-13
Nope, still the same. I cannot access it. :(

Is there anyway to check whats wrong? I tried tracepath, i believe it did not finish, does this mean that my ISP is blocking it?

zyper@desktop:~$ tracepath addons.mozilla.org
 1:  desktop                                             0.113ms pmtu 1500
 1:  122.52.32.1.pldt.net                                359.655ms 
 1:  122.52.32.1.pldt.net                                291.892ms 
 2:  210.5.66.109                                        291.831ms 
 3:  210.213.133.30.static.pldt.net                      287.090ms 
 4:  210.213.128.62.static.pldt.net                      307.883ms 
 5:  210.213.129.33.static.pldt.net                      299.881ms 
 6:  210.213.128.45.static.pldt.net                      291.936ms 
 7:  210.213.131.93.static.pldt.net                      296.594ms asymm  8 
 8:  ix-10-1-0-0.tcore1.LVW-LosAngeles.as6453.net        571.948ms asymm 10 
 9:  no reply
10:  4.68.63.65                                          561.018ms asymm 14 
11:  ae-73-70.ebr3.LosAngeles1.Level3.net                470.657ms asymm 13 
12:  ae-2-2.ebr3.SanJose1.Level3.net                     459.958ms asymm 15 
13:  ae-63-63.csw1.SanJose1.Level3.net                   479.628ms asymm 14 
14:  ae-1-69.edge8.SanJose1.Level3.net                   467.933ms asymm 15 
15:  CWIE-LLC.edge8.SanJose1.Level3.net                  460.001ms asymm 18 
16:  te-8-3.core2.sjc.mozilla.net                        458.303ms asymm 17 
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500

---

### Post by zyperbyte on 2010-10-23
Solved at last. Got the answer from: [http://ubuntuforums.org/showthread.php?t=637208](http://ubuntuforums.org/showthread.php?t=637208)

Solved the problem by lowering MTU size in /etc/ppp/options
There is an entry '# mtu <n>' changed it to 'mtu 1456'
and it worked immediately using wvdial to connect. Saw some topic, where  it recommends to keep on increasing MTU until it stops working, to find  optimal MTU. Optimal MTU provides faster internet. The default 1500 was  to high for my ISP/Setup.

---

