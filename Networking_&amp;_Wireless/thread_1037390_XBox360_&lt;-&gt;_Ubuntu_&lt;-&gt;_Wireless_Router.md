---
title: "XBox360 &lt;-&gt; Ubuntu &lt;-&gt; Wireless Router"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by whaledawg on 2009-01-11
I want to bridge my XBox 360 through one of my ethernet ports to my wireless connection. I've found multiple tutorials and zero that work so far. Some are for earlier versions of Ubuntu and I don't have the same apps in the same place and some are a list of command line operations that don't seem to work since they are designed for 2 NIC cards.

So here's my ifconfig info:

```
eth0      Link encap:Ethernet  HWaddr 00:11:d8:49:fe:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:11:d8:4a:10:ba  
          inet6 addr: fe80::211:d8ff:fe4a:10ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4036 (4.0 KB)  TX bytes:2568 (2.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:e7:35:7b:43  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe35:7b43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6573327 (6.5 MB)  TX bytes:994947 (994.9 KB)
          Interrupt:16 Memory:c1009000-c1009025 

```

I just want every packet from eth1 to be forwarded(bridged) to wlan0 using Ubuntu 8.10.

Any ideas?

---

### Post by whaledawg on 2009-01-12
Really? No one has done this?

---

### Post by superprash2003 on 2009-01-12
you need to enable internet connection sharing .[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) .. or you could use the ICS feature in firestarter

---

### Post by whaledawg on 2009-01-12
That doesn't work at all for me. Following those instructions turns my internet off actually. 

I assumed it was because I'm trying to share through a wireless lan instead of an ethernet card.

---

### Post by whaledawg on 2009-01-12
OK I almost, kinda got this working. I followed [this]("http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN") tutorial and it works...for a while.

More specifically I have to redo those actions every time I start my Xbox up. I just threw
```
#!/bin/bash 
ifconfig eth1 up 
ifconfig eth1 192.168.2.1 
echo "1" > /proc/sys/net/ipv4/ip_forward 
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
```
into a file and execute that every time I want to connect with my 360, but it's a pain in the ***.

Anyone know why when I turn off my Xbox the IP forwarding shuts off? I mean if I do an ifconfig eth1 will no longer have it's static IP assigned to it. Does that seem weird?

---

