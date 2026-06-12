---
title: "Wireless Problem BCM4312/HP Dv2-1020ep"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by ShadowsDML on 2010-10-06
I have an HP Dv2-1020ep with a Broadcom BCM4312 rev 1 with Lucid Lynx installed and I cant get my wireless to work properly.


**lspci**
```
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```**lspci -vnn | grep 14e4**
```
Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```
**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:21:cc:38:fd:9e  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe38:fd9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4930533 (4.9 MB)  TX bytes:711576 (711.5 KB)
          Interrupt:27 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:24:2c:4e:ca:30  
          inet6 addr: fe80::224:2cff:fe4e:ca30/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```**iwconfig**
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.
please help me I'm desperate

---

### Post by ShadowsDML on 2010-10-06
Please I realy nead some help

**uname -r**
```
2.6.32-25-generic

```

---

### Post by Willie11b on 2010-10-14
Same problem here.  I have to go to work but will continue to research this when I get home.  Of course, if you have already solved the problem a quick hint would be nice.....

Will

---

### Post by ShadowsDML on 2010-10-17
Bump

---

### Post by GriffiN on 2010-10-19
this worked for me, hope it works for you.

first

sudo apt-get remove --purge firmware-b43-installer

then

sudo apt-get install firmware-b43-lpphy-installer

worked inmediately

taken from:
[https://bugs.launchpad.net/ubuntu/+s...ey/+bug/655111](https://bugs.launchpad.net/ubuntu/+s...ey/+bug/655111)

---

### Post by lethalfang on 2010-10-19
> **GriffiN said:**
> this worked for me, hope it works for you.

first

sudo apt-get remove --purge firmware-b43-installer

then

sudo apt-get install firmware-b43-lpphy-installer

worked inmediately

taken from:
[https://bugs.launchpad.net/ubuntu/+s...ey/+bug/655111](https://bugs.launchpad.net/ubuntu/+s...ey/+bug/655111)

This fix kinda works, but the wireless connection gets disconnected every couple of hour or so. Do you have the same problem?

---

