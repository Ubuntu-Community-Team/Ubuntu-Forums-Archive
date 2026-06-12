---
title: "URGENT! suddenly can not connect to the internet"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by chaopoch on 2010-05-16
URGENT!!!!
 
Just two hours ago, don't know what happened, I could not download any mail, neither visited any website. I check the cable and adaptor, and found no problems, any solution will be appreciated, thanks a lot.

---

### Post by ronnielsen1 on 2010-05-16
I assume you're connected now. How do you connect? Dial up, dsl, cable? Were all the lights on on the modem?

---

### Post by chaopoch on 2010-05-16
I am using the company network, there is no problem to visit other computers, but just can not connect to the internet, any idea, thanks.

---

### Post by chaopoch on 2010-05-16
The other Windows-base computers can connect to the internet without any problem.

---

### Post by dineshs on 2010-05-16
what do you get when you ping google DNS?```
ping 8.8.8.8 -c5
```

---

### Post by rewyllys on 2010-05-16
> **chaopoch said:**
> URGENT!!!!
 
Just two hours ago, don't know what happened, I could not download any mail, neither visited any website. I check the cable and adaptor, and found no problems, any solution will be appreciated, thanks a lot.
The last post in this thread

[http://ubuntuforums.org/showthread.php?t=1465929&page=2](http://ubuntuforums.org/showthread.php?t=1465929&page=2)

may be pertinent.

---

### Post by chaopoch on 2010-05-17
> **dineshs said:**
> what do you get when you ping google DNS?```
ping 8.8.8.8 -c5
```

The output is 

connect: Network is unreachable

---

### Post by chaopoch on 2010-05-17
> **rewyllys said:**
> The last post in this thread

[http://ubuntuforums.org/showthread.php?t=1465929&page=2](http://ubuntuforums.org/showthread.php?t=1465929&page=2)

may be pertinent.

Thanks, but I am not using wireless network.

---

### Post by chaopoch on 2010-05-17
Refer to the screenshot attached, you can see the ethernet is working, but just no internet connection, I never had this problem before.

BTW, I have network-manager installed, but not wicd.

[ATTACH]157220[/ATTACH]

---

### Post by dineshs on 2010-05-17
If you are using NM
```
gksudo gedit /etc/network/interfaces
``` 
should contain only this 
```
auto lo 
iface lo inet loopback
```   
(Ref  [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager))
Can you ping 192.168.1.1 (hope this is the default gateway)

---

### Post by chaopoch on 2010-05-17
> **dineshs said:**
> If you are using NM
```
gksudo gedit /etc/network/interfaces
``` 
should contain only this 
```
auto lo 
iface lo inet loopback
```   
(Ref  [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager))
Can you ping 192.168.1.1 (hope this is the default gateway)

Thanks for reply.

Yes, there are same lines in /etc/network/interfaces.

The default gateway is 192.168.1.1, but I can not ping it.

[COLOR="Red"]$ ping 192.168.1.1
connect: Network is unreachable[/COLOR]

PS: there is no problem to visit other computers

---

### Post by dineshs on 2010-05-17
what are the results of
```
ifconfig -a
```
and
```
route -n
```

---

### Post by chaopoch on 2010-05-17
> **dineshs said:**
> what are the results of
```
ifconfig -a
```
and
```
route -n
```


$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:18:f3:ec:88:46  
          inet6 addr: fe80::218:f3ff:feec:8846/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:48089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56079748 (56.0 MB)  TX bytes:3137360 (3.1 MB)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:834513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:834513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50958834 (50.9 MB)  TX bytes:50958834 (50.9 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.211.1  Bcast:192.168.211.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.147.1  Bcast:192.168.147.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:72:c6:73  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.147.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.211.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1

---

### Post by chaopoch on 2010-05-17
I can ping the following two IPs now, but still can not browse the web, maybe it is DNS problem, is there any way to fix it? thanks.


[COLOR="Green"]$ ping 203.66.88.89
PING 203.66.88.89 (203.66.88.89) 56(84) bytes of data.
64 bytes from 203.66.88.89: icmp_seq=2 ttl=246 time=119 ms
64 bytes from 203.66.88.89: icmp_seq=3 ttl=246 time=179 ms
64 bytes from 203.66.88.89: icmp_seq=4 ttl=246 time=99.5 ms
^C
--- 203.66.88.89 ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3003ms
rtt min/avg/max/mdev = 99.574/132.840/179.575/34.021 ms

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.968 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.801 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.818 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.824 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.822 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.824 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.815 ms
^C
--- 192.168.1.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6001ms
rtt min/avg/max/mdev = 0.801/0.838/0.968/0.065 ms[/COLOR]

---

### Post by dineshs on 2010-05-18
What is in /etc/resolv.conf?pl post the contents 
```
gksudo gedit /etc/resolv.conf
```
You can try editing the file so that it contains only this
```
nameserver 4.2.2.1
```
other open DNS servers are 8.8.8.8 or  8.8.4.4

---

### Post by chaopoch on 2010-05-18
> **dineshs said:**
> What is in /etc/resolv.conf?pl post the contents 
```
gksudo gedit /etc/resolv.conf
```
You can try editing the file so that it contains only this
```
nameserver 4.2.2.1
```
other open DNS servers are 8.8.8.8 or 8.8.4.4
 
Thanks for reply.
 
The content in /etc/resolv.conf is as follows,
 
nameserver 192.168.1.1
 
I changed it to 4.2.2.1 and saved the file, but after reboot, there is still no internet connection, I check /etc/resolv.conf and find the modification I made is restored to 192.168.1.1

---

### Post by dineshs on 2010-05-18
Can you try configuring NM manually, and give DNS as 4.2.2.1 ?

---

