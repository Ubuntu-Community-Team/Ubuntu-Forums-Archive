---
title: "second network interface doesn't work"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by dimit16 on 2010-07-03
Hi all,

I have two simultaneous active mobile connections through my two mobile phones and  USB data cables. Yet I can only send/receive with one connection.

Each of the phone modems have a node in /dev, namely ttyACM0 and ttyACM0. So the modems are detected correctly.
After setting up two dial-up connections with the two modems I have two ip's. Ifconfig-a confirms this:

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.10.219.60  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:15209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:17321029 (17.3 MB)  TX bytes:1308173 (1.3 MB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:10.10.198.137  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 B)  TX bytes:97 (97.0 B)

So the network interfaces are running and are up.

When I do a wget with 
'wget --bind-address=10.10.219.60  [http://www.google.com/intl/en_ALL/images/srpr/logo1w.png](http://www.google.com/intl/en_ALL/images/srpr/logo1w.png)' 
 the file is downloaded correctly.
Yet when I do a wget with the other interface ('wget --bind-address=10.10.198.137  [http://www.google.com/intl/en_ALL/images/srpr/logo1w.png](http://www.google.com/intl/en_ALL/images/srpr/logo1w.png)'), the download wont start.
The same problem occurs with ping:
'ping -I 10.10.219.60 [www.google.com]("http://www.google.com")' works fine while 
'ping -I 10.10.198.137 [www.google.com]("http://www.google.com")' doesn't receive anything.

Does anyone know how to make the second interface operational?
Thanks.

---

