---
title: "I am connected to wireless but cannot surf"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by 71GA on 2011-02-04
I have a real problem. When i try to connect my wireless i get message "Connection Established", but i cannot surf. What could this be? I tried to reinstall network manager but nothing... is there any file i can edit or check that is connected to wireless?

I tried to type a command:
```
lshw -C network
``````
*-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:f3:95:e7:57:cc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-25-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90100000-9010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:6f:5f:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.5 latency=0 multicast=yes
       resources: irq:42 ioport:2000(size=256) memory:90010000-90010fff memory:90000000-9000ffff memory:90020000-9002ffff

```I allso tried to type in command ```

ifconfig
```And what i get is:
```
eth0      Link encap:Ethernet  HWaddr 60:eb:69:6f:5f:69  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:fe6f:5f69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2182223 (2.1 MB)  TX bytes:471212 (471.2 KB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5216 (5.2 KB)  TX bytes:5216 (5.2 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f3:95:e7:57:cc  
          inet6 addr: fe80::72f3:95ff:fee7:57cc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11292 (11.2 KB)  TX bytes:5919 (5.9 KB)
```**I hope this is enough info for someone to help me :) **:lolflag:

---

### Post by TBABill on 2011-02-04
Are you able to use the same network connection on another computer and access the net fine? If so, have you checked your Firefox IPv6 setting? You can do so by opening Firefox and typing in ```
about:config
``` and search for IPv6. I can't recall the exact setting but it is something to the effect of *network.dns.something.ipv6 *and it is likely set to false. Double click the entry to true and restart Firefox. 
 
You could also try another browser and see if it works. Chromium is a quick install if your broadband speed is decent. 
 
If neither of those work then you likely have a network issue with your config since you are able to connect. But I would try the easy things first.

---

### Post by dineshs on 2011-02-05
Remove ethernet cable , connect wireless and see if it works.If not please post the results of
```
route -n
```and ```
ping 4.2.2.1 -c3
```

---

### Post by 71GA on 2011-02-05
> **TBABill said:**
> Are you able to use the same network connection on another computer and access the net fine? If so, have you checked your Firefox IPv6 setting? You can do so by opening Firefox and typing in ```
about:config
``` and search for IPv6. I can't recall the exact setting but it is something to the effect of *network.dns.something.ipv6 *and it is likely set to false. Double click the entry to true and restart Firefox. 
 
You could also try another browser and see if it works. Chromium is a quick install if your broadband speed is decent. 
 
If neither of those work then you likely have a network issue with your config since you are able to connect. But I would try the easy things first.
I can use this wireless connection on another laptop allso using ubuntu 10.10... 

And here is all that is connected to ipv6:
[img]http://www.shrani.si/f/3X/Kr/1SQPToPQ/screenshot-1.png[/img]

---

### Post by 71GA on 2011-02-05
> **dineshs said:**
> Remove ethernet cable , connect wireless and see if it works.If not please post the results of
```
route -n
```and ```
ping 4.2.2.1 -c3
```

This is what i get... and it looks baad to me and i am no expert... I remembered a while ago i edited some sort of a file using gedit, now i ve forgot where it is, maybe this file is the solution to the problem but i dont know where to locate it :)

```
ziga@ziga-pc:~$ ping 4.2.2.1 -c3
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_req=1 ttl=246 time=76.0 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=246 time=78.8 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=246 time=77.2 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 76.088/77.378/78.817/1.164 ms
ziga@ziga-pc:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ziga@ziga-pc:~$ ping 4.2.2.1 -c3
connect: Network is unreachable

```

---

### Post by dineshs on 2011-02-05
I assume that you got > 64 bytes from 4.2.2.1: icmp_req=1 ttl=246 time=76.0 mswhen ethernet was connected and > ziga@ziga-pc:~$ ping 4.2.2.1 -c3
connect: Network is unreachable when wireless was connected.
Did you edit /etc/network/interfaces?What do you get for ```
sudo cat /etc/network/interfaces
```and```
sudo dhclient wlan0
```
Does the connection work after running sudo dhclient wlan0?

---

### Post by 71GA on 2011-02-05
> **dineshs said:**
> I assume that you got when ethernet was connected and  when wireless was connected.
Did you edit /etc/network/interfaces?What do you get for ```
sudo cat /etc/network/interfaces
```and```
sudo dhclient wlan0
```Does the connection work after running sudo dhclient wlan0?
I did edit this file, but i eddited another one i cant rememmber... oh and by the way here is the file **/etc/network/interfaces**:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
        wpa-driver wired
        wpa-conf /etc/wpa_supplicant.conf

```And here is the full info (all commands) **while ethernet is connected**.
```
ziga@ziga-pc:~$ ping 4.2.2.1 -c3
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_req=1 ttl=246 time=80.0 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=246 time=79.5 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=246 time=77.5 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 77.535/79.038/80.033/1.105 ms
ziga@ziga-pc:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
ziga@ziga-pc:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:f3:95:e7:57:cc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-25-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90100000-9010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:6f:5f:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.5 latency=0 multicast=yes
       resources: irq:42 ioport:2000(size=256) memory:90010000-90010fff memory:90000000-9000ffff memory:90020000-9002ffff

```I tried to use a command you suggested and it still aint working. Here are the result. 
```
ziga@ziga-pc:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/70:f3:95:e7:57:cc
Sending on   LPF/wlan0/70:f3:95:e7:57:cc
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Oh and while talking... I mentioned before that my wireless was working on another laptop using ubuntu 10.10... well it stopped working there too, whithouth any reason...

---

### Post by dineshs on 2011-02-05
Please run
```
sudo gedit /etc/network/interfaces
```
Edit the file so that it reads only
```
auto lo
iface lo inet loopback
```
restart PC,disconnect ethernet cable,click Network manager icon on right top of the panel and connect wireless.Any progress (post output of route -n)

---

### Post by 71GA on 2011-02-05
> **dineshs said:**
> Please run
```
sudo gedit /etc/network/interfaces
```Edit the file so that it reads only
```
auto lo
iface lo inet loopback
```restart PC,disconnect ethernet cable,click Network manager icon on right top of the panel and connect wireless.Any progress (post output of route -n)

I did that but nothing happens:
```
ziga@ziga-pc:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

---

### Post by TBABill on 2011-02-05
From your lshw -C network output: > driver=rt2800pci This could be your issue. I believe your card needs to use the rt2860sta driver, not the rt2800. I would suggest going into /etc/modules and precede the rt2800 driver items with # so the system will ignore them on boot and add rt2860sta at the end of the file. Edit the file with ```
sudo gedit /etc/modules
``` Then you need to blacklist all the rt28xx items by ```
sudo gedit /etc/modprobe.d/blacklist.conf
``` and add the following to the end of the file ```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
``` Then restart and see if it's working for you.

---

### Post by 71GA on 2011-02-05
> **TBABill said:**
> From your lshw -C network output:  This could be your issue. I believe your card needs to use the rt2860sta driver, not the rt2800. I would suggest going into /etc/modules and precede the rt2800 driver items with # so the system will ignore them on boot and add rt2860sta at the end of the file. Edit the file with ```
sudo gedit /etc/modules
``` Then you need to blacklist all the rt28xx items by ```
sudo gedit /etc/modprobe.d/blacklist.conf
``` and add the following to the end of the file ```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
``` Then restart and see if it's working for you.
File **/etc/modules** was almost empty only had a word **lo** inside, so i left it unchanged, but next code 
```
sudo gedit /etc/modprobe.d/blacklist.conf
```saved my day i added all the listed blacklists to that lists, restarded and it worked.

[SIZE=4]Now can you tell me please, how did you know this? I want to learn more of stuff like this. 
[SIZE=6][SIZE=5]Oh and thank you everyone![/SIZE] [/SIZE] [/SIZE]

---

### Post by TBABill on 2011-02-05
I had a similar issue with my RT2860 and another user (chili555) is highly experienced with wireless issues and had helped someone else with a variation of this fix. I do a lot of searching, reading and just trying to help where I can so I can continue to learn. It's just learning by doing on Linux distros and each distro has its own unique issues and fixes sometimes so it gets interesting and fun. 

I am very happy you got it going. Sometimes printing out that single fix and having it handy will help in case you try another install, are forced to reinstall or just do some distro hopping.

---

### Post by 71GA on 2011-02-05
> **TBABill said:**
> I had a similar issue with my RT2860 and another user (chili555) is highly experienced with wireless issues and had helped someone else with a variation of this fix. I do a lot of searching, reading and just trying to help where I can so I can continue to learn. It's just learning by doing on Linux distros and each distro has its own unique issues and fixes sometimes so it gets interesting and fun. 

I am very happy you got it going. Sometimes printing out that single fix and having it handy will help in case you try another install, are forced to reinstall or just do some distro hopping.

Well i am currently trying to cross compile for ARM9 cores, soooo i think i ll soon create a contribution to Ubuntu comunity. Sooo at the moment reinstalling ubuntu is not an option. Thank you for your advice.

---

