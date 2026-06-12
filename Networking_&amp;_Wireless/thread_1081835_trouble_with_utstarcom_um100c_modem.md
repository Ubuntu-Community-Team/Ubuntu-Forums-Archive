---
title: "trouble with utstarcom um100c modem"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by So-Tex on 2009-02-26
Hello everyone. I'm going to say upfront that I am new to linux. I have a problem with connecting to my wireless internet.  In the log it says 
...
NetworkManager: <warn> pppd_timed_out(): looks like pppd didn't initialize our dbus module
Pppd[5856]: terminating on signal 15
...
Can someone tell me what's wrong?
I hope I am giving enough info and any help would be appreciated.

---

### Post by superprash2003 on 2009-02-27
in your terminal type **ifconfig** and post output.. also post output of **iwconfig**

---

### Post by So-Tex on 2009-02-27
here are the results. actually i have a internet connection right now but i dont know if all the settings are correct. I think my problem might have been with the password and encryption key application. Either way will you still look this over and tell me if it looks right?
Thanks




iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.

------

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:b2:5e:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.6.170.112  P-t-P:172.28.220.130  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:28898 errors:1 dropped:0 overruns:0 frame:0
          TX packets:17552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:42410686 (42.4 MB)  TX bytes:896696 (896.6 KB)

---

### Post by superprash2003 on 2009-03-26
well i dont think you would be able to access your modem with this setup.. are you able to? cause i presume eth0 is connected to the modem , but eth0 doesnt seem to be getting an ip address..

---

