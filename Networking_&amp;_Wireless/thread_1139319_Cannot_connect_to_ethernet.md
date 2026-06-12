---
title: "Cannot connect to ethernet"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by harisankar98 on 2009-04-26
Hi,
    Am using ubuntu 8.10. I am not able to connect to ethernet device.. the weird thing is that sometimes, it works fine!!!! and most of the time it does not..

The network manager icon on the taskbar shows that there are no active valid connections.. it is the same when am able to connect or not..
But when i tried booting from the ubuntu live cd, i was able to see active wired connection at the network-manager and the connection information is saying that it is using driver 'r8169'..
something like that is not shown on ma system.. ( i installed ubuntu on ma system using the same live cd ) ..

ping 192.168.1.1 returns.. connect: unreachable..

now, the weirdest thin.. sometimes am able to ping successfuly and even at that time, the network manager icon shows am disconnected.. last day wen i was connected like this, i upgraded to 9.04.. but wen i rebooted, the connection was gone.. 

Pls help me..

---

### Post by harisankar98 on 2009-04-26
forgot one thing.  the network adapter works fine under vista.. its Realtek RTL8168B/8111B Family PCI-E Gigabit Ethernet ..

ma system is a laptop.. the MSI GX620...

---

### Post by fornix on 2009-04-27
Please paste the output of the following
```
$ ifconfig -a
```

---

### Post by harisankar98 on 2009-04-27
hey... all of a sudden the ethernet worked again and i am now posting this from ma updated Jaunty...

here is ma ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:21:85:48:f0:d7  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe48:f0d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1093 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:929092 (929.0 KB)  TX bytes:264825 (264.8 KB)
          Interrupt:248 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:580 (580.0 B)  TX bytes:580 (580.0 B)

pan0      Link encap:Ethernet  HWaddr d6:7a:3e:f9:9f:33  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.196.134.183  P-t-P:117.196.128.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:883938 (883.9 KB)  TX bytes:214690 (214.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:5e:1e:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-5E-1E-F8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



if i remember correctly, earlier when there was no net, the ifconfig eth0 returned details without the ip, broadcast and netmask..

here is ma    /etc/network/interfaces 

auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up           # line maintained by pppoeconf
provider dsl-provider

---

### Post by harisankar98 on 2009-04-27
forgot one more thing.. now the network manager is showing the connection and the connection information is showing that it is using the r8169 driver.. 

lemme reboot once again and check if its not working..

---

### Post by harisankar98 on 2009-04-27
rebooted.. and not working.. :D.. this is weird.. this is the output of ifconfig -a now..

eth0      Link encap:Ethernet  HWaddr 00:21:85:48:f0:d7  
          inet6 addr: fe80::221:85ff:fe48:f0d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3204 (3.2 KB)
          Interrupt:248 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr aa:ad:aa:f1:f3:b7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:5e:1e:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-5E-1E-F8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


see the difference..

---

### Post by fornix on 2009-04-28
When you are not connected, does a manual down and up of your interface help?

```
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 up
```

If that doesn't work, next step would be to manually edit your /etc/network/interfaces file and add the following entry

```
iface eth0 inet dhcp
```

Assuming you are using DHCP instead of manual ip address.

Then, try disabling (down) and enabling(up) your network interface. The first commands.

---

