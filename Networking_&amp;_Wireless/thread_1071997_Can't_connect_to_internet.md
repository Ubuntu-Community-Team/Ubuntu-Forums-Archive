---
title: "Can't connect to internet"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by toolow50 on 2009-02-16
friebel@friebel:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:21:85:c8:f6:72
inet addr:69.23.99.82 Bcast:69.23.103.255 Mask:255.255.248.0
UP BROADCAST RUNNING MULTICAST MTU:576 Metric:1
RX packets:692 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:42422 (42.4 KB) TX bytes:692 (692.0 B)
Interrupt:219

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:64 errors:0 dropped:0 overruns:0 frame:0
TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5152 (5.1 KB) TX bytes:5152 (5.1 KB)



cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by bgates on 2009-02-17
It looks like you are receiving and sending data without errors or packet loss.  How many ways are you trying to access the internet?  If just a browser, clear the browser's cache and restart the browser.  Or, try a different browser.  Better yet, try to ping something.  In terminal, ping google.com -c4 

(for example.).

---

### Post by superprash2003 on 2009-02-17
your MTU value is 576 which is pretty low.. try changing it [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html) /.. also try to open [http://74.125.45.100](http://74.125.45.100)

---

### Post by odium1 on 2009-02-17
> **superprash2003 said:**
> your MTU value is 576 which is pretty low.. try changing it [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html) /.. also try to open [http://74.125.45.100](http://74.125.45.100)

i use your site almost daily lol. good stuff.

---

### Post by superprash2003 on 2009-02-19
thanks :)

---

