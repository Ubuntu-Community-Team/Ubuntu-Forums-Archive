---
title: "Wireshark~"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by xideadfishix on 2010-04-04
Laptop A
wlancard intel 5100agn
ip: 157.190.70.101

Laptop B
wlancard senao Senao NL-2511CD PLUS EXT2 > running on hostap driver
ip: 157.190.70.100

Scenario
Laptop A:   sudo ping -f 157.90.70.228
Laptop B:   airmon-ng start wlan2
Laptop B:   on wireshark and monitor wlan2.

Issue
I am able to captured the ECHO (ping) request from 157.190.70.101(Laptop A) but in the next line right after, there is another packet captured which i believe is the Ack for the request earlier.

Question
How come it does not display the right protocol being used in the ack(in this case icmp) and the info not being labeled as ECHO (ping) ack(in this case, being stated in the info as Acknowledgement, Flags =.......) ?


I'm sure someone out there have encountered this before and solved it.~ i tried searching around but i cant seem to find anything helpful. And correct me if im wrong as i'm not very familiar with the protocols and stuff. 

p/s~ i attached two image files just in case it is any good. thank you~

---

### Post by xideadfishix on 2010-04-05
problem solved~ it has got something to do with my configurations~

---

