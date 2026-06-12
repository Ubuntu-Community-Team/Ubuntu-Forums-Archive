---
title: "Setting up wlan0"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by tweaku on 2011-11-01
I can't set up the wireless network. I try to do this for 5 days but no results. There are my settings.
**lspci:**
```
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```**ifconfig -a:**
```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:b4:5a:71  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feb4:5a71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7726671 (7.7 MB)  TX bytes:1223692 (1.2 MB)
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:14:43:e5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```**iwconfig:**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"TP-LINK_B35646"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```I had install firmware-b43-installer.
When I try to say:
**ifup wlan0**
system answer:
RTNETLINK answers: Operation not possible due to RF-kill[/code]
How to set it up?

---

### Post by matt_symes on 2011-11-01
Hi

Is it blocked ?

Open a terminal and type

```
sudo rfkill list
```

Post back here. If wlan0 is block by a softblock then type

```
sudo rfkill unblock all
```

If a hard block then check for a switch or in the BIOS.

If you need to install rfkill

```
sudo apt-get install rfkill
```

It may also be an idea to post the output of

```
sudo lshw -c network
```

Kind regards

---

### Post by tweaku on 2011-11-01
Softblock is off but hardblock is on. In BIOS I can't find option to change it :( Can I change it using other way?

---

### Post by matt_symes on 2011-11-02
Hi

Is there a switch to remove the hard block on your laptop ?

Kind regards

---

