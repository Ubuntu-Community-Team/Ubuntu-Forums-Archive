---
title: "Multiple MAC addresses on one computer (Virtual Network)"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by JeSTeRFLA on 2011-09-15
here is what i need to know how to do:
i have 16 ips on my modem my ISP "DOES NOT SUPPORT Static Routes" SO heres what i wanted to do:

i want to set up a Virtual Network with 10 DIFFERENT Mac Addresses
VPN doesn't work properly "don't know why either" anyways to set this up on the box side to make this one box look to the modem to be 10 boxes? 
:popcorn:

---

### Post by e79 on 2011-09-15
Mind to clarify a bit what you intend to do since it does not make any sense ?

Few things :
First of all, as far as I know (maybe someone will correct me) Virtual Network are composed of IPs, not MAC address.
We don't know what kind of VPN you are trying to install and what exactly you want to achieve when saying "to set this up on the box side to make this one box look to the modem to be 10 boxes?"

Give more details if you want help.

---

### Post by JeSTeRFLA on 2011-09-15
i can allocated ips to mac's via modem console all im trying to do is allocate 10 of my 16 ips to the box bypassing the need for static routes

I Am Open For Suggestions

---

### Post by e79 on 2011-09-15
So you want to make some IP reservation for your MAC addresses ? Or you want all your 10 external IPs to be forwarded to your computer a bit like:

Example with fictive IPs:

External IP           --> Internal IP     
10.0.0.2 -->       192.168.0.10
10.0.0.3 -->       192.168.0.10
10.0.0.4 -->       192.168.0.10
10.0.0.5 -->       192.168.0.10
etc etc etc

Could you simply do a port forwarding as shown above in your modem/router perhaps ?

---

### Post by JeSTeRFLA on 2011-09-16
> **e79 said:**
> So you want to make some IP reservation for your MAC addresses ? Or you want all your 10 external IPs to be forwarded to your computer a bit like:

Example with fictive IPs:

External IP           --> Internal IP     
10.0.0.2 -->       192.168.0.10
10.0.0.3 -->       192.168.0.10
10.0.0.4 -->       192.168.0.10
10.0.0.5 -->       192.168.0.10
etc etc etc

Could you simply do a port forwarding as shown above in your modem/router perhaps ?


i tried that it actually will only lemme forward one ip per mac. seeing as how i dont have 10 macs on this box i can only forward one ip

i just want all my ips on the box its getting frustrating

---

### Post by Lisiano on 2011-09-16
I found a project called MultiMac. Maybe this could help?
[http://sourceforge.net/projects/multimac/](http://sourceforge.net/projects/multimac/)
[http://www.primianotucci.com/default.php?view=57](http://www.primianotucci.com/default.php?view=57)

---

### Post by HugoSerrano on 2011-09-16
if you do:
ifconfig eth0:1 10.0.0.1 netmask 255.255.255.0
ifconfig eth0:2 10.0.0.2 netmask 255.255.255.0
...
ifconfig eth0:10 10.0.0.10 netmask 255.255.255.0

you can get 10 ip's on your interface.

Is that what you want?

regards!

---

### Post by e79 on 2011-09-16
> **JeSTeRFLA said:**
> i tried that it actually will only lemme forward one ip per mac. seeing as how i dont have 10 macs on this box i can only forward one ip

i just want all my ips on the box its getting frustrating

So...why are you trying to forward IP to MAC when you can simply forward External IPs to an internal IP as I suggested ?

---

### Post by JeSTeRFLA on 2011-09-16
> **Lisiano said:**
> I found a project called MultiMac. Maybe this could help?
[http://sourceforge.net/projects/multimac/](http://sourceforge.net/projects/multimac/)
[http://www.primianotucci.com/default.php?view=57](http://www.primianotucci.com/default.php?view=57)
   PERFECT just what i was lookin for too THANK YOU

---

### Post by Lisiano on 2011-09-17
Sine your problem is solved, please mark the thread as solved in the Thread Tools above.

---

### Post by JeSTeRFLA on 2011-09-17
wasn't solved SO.... lol NOW i need to know how to setup a tap0 connection i guess :\

is that suppost to go in the etc/network/interfaces file?





jester-section-8 ~ # ifconfig tap1 hw ether 00:1b:b9:c0:a8:a9
SIOCSIFHWADDR: No such device
jester-section-8 ~ # ifconfig tap1 hw ether 2e:de:1c:5d:c6:64
SIOCSIFHWADDR: No such device
jester-section-8 ~ # ifconfig tap1 hw ether 2e:de:1c:5d:c6:68
SIOCSIFHWADDR: No such device

---

### Post by Lisiano on 2011-09-18
You did run ```
./multimac 10
``` right? Post the output of this command AFTER running the command above```
ifconfig -a
```

---

### Post by JeSTeRFLA on 2011-09-18
yes i did im down to the 
ifconfig tap1 hw ether <New MAC address> on that site with this error reporting 

jester-section-8 ~ # ifconfig tap1 hw ether 00:1b:b9:c0:a8:a9
SIOCSIFHWADDR: No such device

---

### Post by Lisiano on 2011-09-20
I need the output of this command after you run ./multimac 10
```
ifconfig -a
```
Else I have no ground to work on.

---

### Post by JeSTeRFLA on 2011-09-25
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:c0:a8:c9
          inet addr:108.75.X.X  Bcast:108.75.X.X  Mask:255.255.255.240
          inet6 addr: fe80::21b:b9ff:fec0:a8c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:508271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:516841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:75930515 (75.9 MB)  TX bytes:47846307 (47.8 MB)
          Interrupt:19 Base address:0xdead

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3914481 (3.9 MB)  TX bytes:3914481 (3.9 MB)

tap0      Link encap:Ethernet  HWaddr da:6a:89:eb:b0:9a
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap1      Link encap:Ethernet  HWaddr 7a:c4:9b:f7:d1:8c
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap2      Link encap:Ethernet  HWaddr da:26:28:a3:24:b0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap3      Link encap:Ethernet  HWaddr aa:15:8f:1a:06:10
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap4      Link encap:Ethernet  HWaddr ea:2b:c7:3e:e3:a1
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap5      Link encap:Ethernet  HWaddr 4e:d2:3c:f1:f9:c2
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap6      Link encap:Ethernet  HWaddr fa:04:27:9c:83:6e
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap7      Link encap:Ethernet  HWaddr ea:97:bc:4d:4e:73
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap8      Link encap:Ethernet  HWaddr 26:90:84:62:03:99
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap9      Link encap:Ethernet  HWaddr c2:6c:01:34:8a:77
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap10     Link encap:Ethernet  HWaddr fe:1f:36:8e:16:f3
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



ALL THAT is set up
how do i change the tap1-10 bcast: from 108.255.255.255 to the real bcase ip?

---

### Post by Lisiano on 2011-09-26
```
sudo ifconfig tap# broadcast 255.255.255.255
```
Substitute tap# with the real tap and 255.255.255.255 to the real broadcast.

---

