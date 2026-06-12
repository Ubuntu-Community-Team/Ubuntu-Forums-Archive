---
title: "Programs cannot reach network"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by ntaforge on 2009-05-18
Hello

I just finished a fresh install of 8.10 and for some reason I cannot get any of my programs to reach the network. Now Firefox and Thunderbird can get to the net but my games bzflag Armagetron etc. cannot find their master servers and I'm sure transmission is having the same problem.

---

### Post by ntaforge on 2009-05-18
bump

---

### Post by cariboo on 2009-05-19
Do you connect to the internet through a router? if you have any port forwarding setup, you may have to change the setup as your ip address may have changes.

---

### Post by ntaforge on 2009-05-21
I tried that but I'm still not getting out

---

### Post by superprash2003 on 2009-05-22
post output of **ifconfig **from the terminal

---

### Post by ntaforge on 2009-05-25
[PHP]eth0      Link encap:Ethernet  HWaddr 00:a0:d1:82:0e:79  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92 (92.0 B)  TX bytes:92 (92.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:13:e6:a4  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe13:e6a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16943640 (16.9 MB)  TX bytes:4561868 (4.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-13-E6-A4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/PHP]

---

### Post by ntaforge on 2009-05-25
Bump

---

### Post by Iowan on 2009-05-25
Connecting via wireless (since eth0 has no IP address)? 
What are results of **route -n** and contents of */etc/resolv.conf*?

---

### Post by ntaforge on 2009-05-26
[PHP]
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
[/PHP]

[PHP]domain domain_not_set.invalid
search domain_not_set.invalid
nameserver 192.168.0.1
nameserver 68.94.156.1[/PHP]

---

### Post by Iowan on 2009-05-26
The routing table looks kosher to my untrained eye - /etc/resolv.conf looks a bit unusual with the "domain_not_set.invalid" messages. I presume 192.168.0.1 is your router...

---

### Post by ntaforge on 2009-05-27
Yes it is

---

### Post by ntaforge on 2009-06-01
bump

---

### Post by ntaforge on 2009-06-03
and again BUMP!

---

### Post by ntaforge on 2009-06-17
ok so alittle progress

I had virtualbox installed and it seems that it doesn't like anything related to networking, which I really didn't need it so I uninstalled.  Now some of my programs are working now but I have found that I have to drop my firewall on my router. I've tried to forward the ports to the apps but STILL doesn't work! so is there a port or protocol that I need to enable to get this to work?

Thanks

---

### Post by ntaforge on 2009-06-18
bump

---

