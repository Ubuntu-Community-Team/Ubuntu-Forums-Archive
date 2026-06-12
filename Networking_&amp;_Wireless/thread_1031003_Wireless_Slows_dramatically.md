---
title: "Wireless Slows dramatically"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by jdfoote on 2009-01-04
I just set up a new wireless router, and now I'm having some troubles with my network. My Windows box connects without any problems, but my Ubuntu machine keeps having issues. The connection will be fine for a while, then slow to a crawl, and then it will be fine again.

Here is the output from ifconfig:

```
wlan0 Link encap:Ethernet  HWaddr 00:11:a3:04:c2:5a  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:a3ff:fe04:c25a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23286827 (23.2 MB)  TX bytes:5544194 (5.5 MB)

```

I am pretty helpless when it comes to networking, so any input would be greatly appreciated.

---

### Post by superprash2003 on 2009-01-05
is it slow browsing speed for you?? in that case you could try changing DNS servers to opendns .. their ips are 208.67.222.222 and 208.67.220.220 [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by jdfoote on 2009-01-05
I'm also having problems when getting updates from the Ubuntu servers. Do those need to be resolved by the DNS as well, or does that mean that I have a different problem?

I have switched to OpenDNS, and it seems to be helping so far...

---

### Post by superprash2003 on 2009-01-06
under sytem->admin->software sources, try changing download from  to "MAIN server"

---

