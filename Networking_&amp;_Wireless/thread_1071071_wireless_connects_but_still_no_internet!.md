---
title: "wireless connects but still no internet!?"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by Sketches on 2009-02-15
i'm kinda a newbie so no overboard comments please.

i tried the live version of Ubuntu, mint, fedora, mandriva one, etc. all have the same wireless issue. i don't have a wired connection so please keep that in mind.

i'm using a dell studio 1537 with the 
intel WIFI link 5100 (802.11 a/b/g/n 1x2 1/2 minicard)

in all distros the wireless card recognises signal and networks and it connects and says it is connected. however all the browsers get locked in an infinite cycle of loading nothing with no error message the same with package downloads. only in mandriva did an error message appear.
it said the wireless card worked but some broadcom thing extraneous to the wireless card was wrong. i lost that live cd so i can't get the actual error message.

thanks!!!

---

### Post by frklin on 2009-02-15
During the connection, make sure you have the correct DNS servers. Run in terminal:
```
cat /etc/resolv.conf
```

---

### Post by Sketches on 2009-02-16
> **frklin said:**
> During the connection, make sure you have the correct DNS servers. Run in terminal:
```
cat /etc/resolv.conf
```

no difference lists correct servers, connects then nothing. same as always

---

### Post by Sketches on 2009-02-18
The problem is still there!!!! Someone help...
Its the only problem between me and linux!!!

---

### Post by superprash2003 on 2009-02-18
please post output of **ifconfig** and **iwconfig** from the terminal

---

### Post by Sketches on 2009-02-18
ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:22:19:de:48:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:7200 (7.2 KB)  TX bytes:7200 (7.2 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:0d:be:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-22-FB-0D-BE-B4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11abgn  ESSID:"WaveLAN Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:A9:B5:9E:D0   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality=30/100  Signal level:-73 dBm  Noise level=-85 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions.

---

### Post by superprash2003 on 2009-02-19
your wlan0 isnt getting an ip .. in your terminal type **sudo dhclient wlan0** and then post output of **ifconfig** again

---

### Post by Sketches on 2009-02-19
> **superprash2003 said:**
> your wlan0 isnt getting an ip .. in your terminal type **sudo dhclient wlan0** and then post output of **ifconfig** again

ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:22:19:de:48:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:7200 (7.2 KB)  TX bytes:7200 (7.2 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:0d:be:b4  
          inet addr:137.43.232.131  Bcast:137.43.233.255  Mask:255.255.254.0 
          inet6 addr: fe80::222:fbff:fe0d:beb4/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2862 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:355660 (355.6 KB)  TX bytes:12307 (12.3 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-22-FB-0D-BE-B4-65-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

ubuntu@ubuntu:~$

---

### Post by superprash2003 on 2009-02-20
thats good.. now wlan0 has an ip 137.x.x.x .. are you able to access the internet now?? try opening [http://74.125.67.100](http://74.125.67.100)

---

### Post by Sketches on 2009-02-22
not any adress's i checked. would the number code make any difference?

---

### Post by Sketches on 2009-02-22
> **superprash2003 said:**
> thats good.. now wlan0 has an ip 137.x.x.x .. are you able to access the internet now?? try opening [http://74.125.67.100](http://74.125.67.100)

not the address's i tried... would the number code be differnet?

---

### Post by Sketches on 2010-05-09
i just turned off ipv6 in firefox! now fine

---

