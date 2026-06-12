---
title: "wlan help!!!!!!!!"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by luigi94 on 2009-05-25
i installed the driver for my wireless card then i connected my pc to my home wireless network i put the password in and i connected to it.
then i punched in terminal :
sudo pppoeconf     
and i completed the settings and my connection was working perfect.
after that i restarted my pc and my internet wasn't workig and when i clicked on network manager it said

Wireless network 

device in onmounted

how can i connect to my wireless modem?

---

### Post by jtdeloach10 on 2009-05-25
When you shutdown, did you shutdown correctly? I remember in XP if you did not shutdown properly settings would not be saved, I am not sure if this applies here. If you for instance lost power, forced your computer off, it cannot properly save this info, and this might be the problem.

---

### Post by superprash2003 on 2009-05-26
post output of **ifconfig** and **iwconfig** from the terminal

---

### Post by luigi94 on 2009-05-26
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:15:f2:75:b4:5b  
          inet6 addr: fe80::215:f2ff:fe75:b45b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104806 (104.8 KB)  TX bytes:15455 (15.4 KB)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8184 (8.1 KB)  TX bytes:8184 (8.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:79.47.132.169  P-t-P:151.99.26.97  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:100890 (100.8 KB)  TX bytes:11589 (11.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:f2:10:be:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-F2-10-BE-35-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

luigi@luigi-laptop:~$ 

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by superprash2003 on 2009-05-26
cclick on the networking icon on the top bar , you should see a list of wifi networks..

---

### Post by luigi94 on 2009-05-26
that is my problem instead of listing my wireless networks it says
[COLOR=Navy]device is unmanaged[/COLOR]

---

### Post by luigi94 on 2009-05-26
i took a screen shot if u want i can uplaod it 4 u

---

### Post by luigi94 on 2009-05-26
i got my wireless working again using wicd instead of network manager but i haven't restarted yet

---

### Post by luigi94 on 2009-05-26
i just restarted and i punched in terminal sudo pon dsl-provider and now my wireless connection is working fully . thank 4 your help

---

