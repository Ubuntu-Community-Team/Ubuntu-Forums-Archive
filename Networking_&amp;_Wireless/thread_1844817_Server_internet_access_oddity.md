---
title: "Server internet access oddity"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by cs1jrw on 2011-09-15
Hi

Just upgraded a Ubuntu 9 server to 10.04LTS and have a problem I can't get my head around. Basically I can't get a two way dialog going with the internet ie can't browse (using lynx) or get a file content using php. However I can SSH from server to a remote server and also SSH to my server from the remote. Ditto with ping (both IP address and canonical, so DNS is OK). I can access apache on my server from remote.

When I start lynx it usually fails with a timeout and Unable to connect to remote host message, but just occasionally can get a reply from lynx.isc.org.

Any suggestions for further tests etc?

Thanks
--
Richard

---

### Post by SeijiSensei on 2011-09-16
Check that DNS is correctly configured.  Take a look at /etc/resolv.conf to make sure.

---

### Post by cs1jrw on 2011-09-17
Thanks, seems to be OK:
nameserver 192.168.1.1
which is the address of my adsl router...
--
Richard

---

### Post by varunendra on 2011-09-18
What if you change it to a different one, like Google's 4.2.2.2 and 4.2.2.4 for example?

Further, can we have a look at outputs of:
```
ping google.com
ping archive.ubuntu.com
ifconfig
```

---

### Post by cs1jrw on 2011-09-18
Hi. Briefly thought there was some success- changed nameserver entry to 8.2.2.2 as suggested and was able to start lynx after a brief delay. However, a second try failed. 
Output of pings and ifconfig and attempt to run lynx as below:


PING google.com (209.85.229.99) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (209.85.229.99): icmp_seq=1 ttl=53 time=30.3 ms
64 bytes from [www.google.com](www.google.com) (209.85.229.99): icmp_seq=2 ttl=53 time=30.6 ms
64 bytes from [www.google.com](www.google.com) (209.85.229.99): icmp_seq=3 ttl=53 time=30.7 ms
64 bytes from [www.google.com](www.google.com) (209.85.229.99): icmp_seq=4 ttl=53 time=31.1 ms

--- google.com ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8012ms
rtt min/avg/max/mdev = 28.983/31.187/34.123/1.308 ms

PING archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (91.189.88.31): icmp_seq=1 ttl=54 time=26.2 ms
64 bytes from archive.ubuntu.com (91.189.88.31): icmp_seq=2 ttl=54 time=23.1 ms
64 bytes from archive.ubuntu.com (91.189.88.31): icmp_seq=3 ttl=54 time=24.5 ms
64 bytes from archive.ubuntu.com (91.189.88.31): icmp_seq=4 ttl=54 time=24.9 ms

--- archive.ubuntu.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7010ms
rtt min/avg/max/mdev = 23.138/24.425/26.225/0.988 ms

eth0      Link encap:Ethernet  HWaddr 00:e0:4c:fc:04:b3  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fefc:4b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44181048 (44.1 MB)  TX bytes:54169991 (54.1 MB)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57974 (57.9 KB)  TX bytes:57974 (57.9 KB)

lynx
Looking up lynx.isc.org
Making HTTP connection to lynx.isc.org
Alert!: Unable to connect to remote host.

lynx: Can't access startfile [http://lynx.isc.org/](http://lynx.isc.org/)

---

### Post by varunendra on 2011-09-18
Everything with ifconfig or ping timings seem satisfactory to me, so no clues yet. I have absolutely no experience with lynx, so cant say if there is or can be anything specific to it.

What is the brand and model of your router? Also, please try disabling IPv6 to see if some improvement occurs:
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

or,

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html) (follow the third method, replacing gedit with your favourite text editor)

---

### Post by pyro-ns on 2011-09-19
This bares quite a few similarities to [my problem]("http://ubuntuforums.org/showthread.php?t=1846064")... Have you done any apt-get update's lately?

---

### Post by chili555 on 2011-09-19
Do you get a connection with:```
lynx http://www.google.com
```What does this tell us?```
cat /etc/network/interfaces
```Thanks.

---

### Post by cs1jrw on 2011-09-21
Do I get a connection with google url? Not really - After some initial activity lynx asks me if I am happy to save cookies from Google. I say yes, then connection times out as before

The cat command gives:
# The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet dhcp

---

