---
title: "DHCP works, but can't ping anything!"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by tcostello on 2009-02-14
As you can see I'm new to the whole Ubuntu thing, if I'm missing something extremely obvious I apologize in advance.

I have a Lenovo T400 with an Intel 5100 Wireless card. Was able to access the internet and got VMWare Server 2 working great with Ubuntu 8.10 64-bit, couldn't be happier so far. Until today I ran an update and although I can still connect to my wireless network, I'm not able to ping my router or any other device on the network. Of course, the internet is down as well, rendering my laptop near useless for what I use it for :)

I used the Internet Connection Sharing guide at [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) and it also worked perfectly getting my Xbox connected to the network a few weeks back. Perhaps a configuration is off due to the kernal being updated? I was able to connect to the network, send and receive packets and even get an IP address, but unable to communicate with anything on my network. Any ideas are most appreciated, if there's any more information I can provide please let me know.

Thanks!

---

### Post by tcostello on 2009-02-14
bump

---

### Post by superprash2003 on 2009-02-14
please post output of **ifconfig** from the terminal

---

### Post by tcostello on 2009-02-14
The requested output is below. I ended up re-installing Ubuntu today and everything worked great, restarted a few times, then did the internet sharing thing again. Sure enough it broke instantly! So if there's a way I can un-do the modifications I made to the iptable and get the internet up that would be fine, as long as I can get to the internet I'll live; sharing is just an added bonus

Thanks again!

eth0      Link encap:Ethernet  HWaddr 00:21:86:9e:17:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fc200000-fc220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2832 (2.8 KB)  TX bytes:2832 (2.8 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.130.1  Bcast:172.16.130.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.98.1  Bcast:172.16.98.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:46:73:c8  
          inet addr:10.11.12.13  Bcast:10.11.12.15  Mask:255.255.255.240
          inet6 addr: fe80::221:5dff:fe46:73c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34638 (34.6 KB)  TX bytes:1124 (1.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5D-46-73-C8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by tcostello on 2009-02-14
Also, the wlan0 ip address and subnet mask is correct, I may not be the wisest ubuntu user but I can use vlsm :)

---

### Post by tcostello on 2009-02-15
After another re-install of Ubuntu, the problem is solved! Instead of using the commands I used Firestarter and it did all the hard work, plus it did not break my network.

---

### Post by superprash2003 on 2009-02-15
incase you come across the same problem again.. just flush your iptables and it should work. you dont need to reinstall ubuntu all over again .. [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

