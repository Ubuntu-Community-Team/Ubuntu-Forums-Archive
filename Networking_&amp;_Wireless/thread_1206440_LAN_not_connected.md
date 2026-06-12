---
title: "LAN not connected"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by kaustubh.bansal on 2009-07-07
I have a broadband connection that requires user name and password at home, and a regular LAN connection at college.
My connection at college used to run fine. I went home for a few days, i used **pppoeconf** utility to setup the connection at home (default values everywhere). Now when I'm back at college, my LAN connection does not work. 
How can I now connect to it? Is there any way i could make this LAN connection as default and whenever I want to use broadband, I can switch over to it?

---

### Post by enli on 2009-07-07
As you are manually using the pppoeconf to connect to internet there should not be any problem. Try re-configuring the LAN settings for your college e.g. IP address, subnet mask and proxy server if applicable.

---

### Post by kaustubh.bansal on 2009-07-07
I use **sudo pon dsl-provider** to connect to broadband. What do I do to connect to the LAN? I have made the changes to proxy settings for college but I.P. address should be automatically allotted.
But instead there's a LAN symbol at system tray with a small cross beneath it. That means LAN is definitely not connecting..

---

### Post by superprash2003 on 2009-07-07
please post output of ifconfig from the terminal , to get an idea of your interfaces

---

### Post by kaustubh.bansal on 2009-07-08
> **superprash2003 said:**
> please post output of ifconfig from the terminal , to get an idea of your interfaces

Here's the output. I have a wireless card and a LAN card on my system
```

kaustubh@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:14:a5:f7:e3:87  
          inet addr:172.16.1.138  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fef7:e387/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1044 errors:0 dropped:0 overruns:0 frame:246
          TX packets:680 errors:7 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:841867 (841.8 KB)  TX bytes:173594 (173.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)



```

---

### Post by superprash2003 on 2009-07-09
hmm..oinly one of those interfaces seem to be up.. post output of
1)iwconfig
2)lshw -C network

---

### Post by kaustubh.bansal on 2009-07-10
> **superprash2003 said:**
> hmm..oinly one of those interfaces seem to be up.. post output of
1)iwconfig
2)lshw -C network

Here's the output
```

kaustubh@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:205  Noise level:161
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.


```

```

kaustubh@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:f7:e3:87
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=172.16.1.138 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:17:08:40:a0:36
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5788-v3.26 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:c9:d5:ee:50:b5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by enli on 2009-07-10
This may sound silly, but right click computers icon in system tray near date and make sure "Enable Networking" is ticked.

---

### Post by kaustubh.bansal on 2009-07-10
> **enli said:**
> This may sound silly, but right click computers icon in system tray near date and make sure "Enable Networking" is ticked.

Please be assured its ticked :)

---

### Post by enli on 2009-07-10
post output of
```
ifconfig -a
```

**Edit ** : Connect to some LAN or another computer temporary with cross-over cable and try
```

sudo ifconfig eth0 192.168.1.5
sudo ifconfig eth0 up

```

---

### Post by kaustubh.bansal on 2009-07-10
```
kaustubh@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:08:40:a0:36  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

eth1      Link encap:Ethernet  HWaddr 00:14:a5:f7:e3:87  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1377 errors:0 dropped:0 overruns:0 frame:126
          TX packets:678 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:873445 (873.4 KB)  TX bytes:143531 (143.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)

pan0      Link encap:Ethernet  HWaddr a2:2f:a0:f3:01:0e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Ethernet is DISABLED. I tried setting up the connection like you said but that damn red cross below the network symbol does not budge!!

---

### Post by enli on 2009-07-10
Hmm, that means your network card is working. The only problem is that it is not managed by Network-Manager. After typing those 2 commands I asked, did it give any type of error/message?

Could you please post output of
```

sudo cat /etc/NetworkManager/system-connections/Ethernet
cat /etc/NetworkManager/nm-system-settings.conf
cat /etc/network/interfaces

```

Also if possible tell us more information about the network where you are trying to see if networking work. e.g. Your static ip, gateway, netmask. We can try to configure via command-line and lets see what happens.

---

### Post by kaustubh.bansal on 2009-07-10
> Hmm, that means your network card is working. The only problem is that it is not managed by Network-Manager. After typing those 2 commands I asked, did it give any type of error/message?
No, it didn't give any message at all

```
kaustubh@ubuntu:~$ sudo cat /etc/NetworkManager/system-connections/Ethernet
cat: /etc/NetworkManager/system-connections/Ethernet: No such file or directory

```

```
kaustubh@ubuntu:~$ cat /etc/NetworkManager/nm-system-settings.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


```


```
kaustubh@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```

I'm trying to connect at my college, We have a proxy server
I.P: 172.16.0.8, Port: 8888

These static configurations work in Windows
I.P.: 172.16.1.xxx
Bcast: 172.16.1.255
Mask: 255.255.255.0

I hope this is what you've asked for :)

---

### Post by enli on 2009-07-10
```
sudo gedit /etc/network/interfaces
```

Delete existing contents and paste following
```

auto lo
iface lo inet loopback

iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

iface eth0 inet static
name Ethernet
address TYPEYOURSTATIC-ADDRESS
netmask 255.255.255.0
broadcast 172.16.1.255
network YOURNETWORKGATEWAYHERE

auto eth0

```

Replace your IP and if are given a gateway address change it too. If you connect without gateway address remove line "network YOURNETWORKGATEWAYHERE". After updating file

```
sudo /etc/init.d/networking restart
```

See if connection works now.

---

### Post by kaustubh.bansal on 2009-07-10
Please forgive my ignorance,
Windows says that 
Default Gateway: 172.16.1.254
Is this what I have to specify?
I tried but it didnt work..
I also tried without that option but still it didn't connect?

Will it ever work :confused: ??

---

