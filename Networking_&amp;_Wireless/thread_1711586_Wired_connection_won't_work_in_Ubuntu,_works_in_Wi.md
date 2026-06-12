---
title: "Wired connection won't work in Ubuntu, works in Win7."
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by ratdog on 2011-03-21
Hello,

I am having difficulties connecting to my router with my Ubuntu 10.04 laptop.  Wireless works fine and I can get a wired connection when I boot into Windows 7.  

In Network Connections there is no Auto eth0 listing and when I create a wired connection, as soon as I enter details, the 'Apply' button grays out!  Am I missing some permissions?

Here is some terminal output:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:23:5a:d2:1f:13  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fed2:1f13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:230964 (230.9 KB)  TX bytes:82165 (82.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1280 (1.2 KB)  TX bytes:1280 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:56:ca:dc  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe56:cadc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5701 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6371421 (6.3 MB)  TX bytes:830294 (830.2 KB)
```

lspci
```
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
```

Thanks for you help!

---

### Post by conneco on 2011-03-21
To be honest your output from ifconfig looks like your Network card has a connection its pulled the ip of 192.168.1.67, what happens if you try and ping your router

if your on 192.168.1.67 then your router will usually have the ip of 192.168.1.1 or 192.168.1.254 in a terminal type
ping 192.168.1.1

and see if it fails or dies

---

### Post by ratdog on 2011-03-21
Here is the output of the ping:

```
@ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.67 icmp_seq=2 Destination Host Unreachable
From 192.168.1.67 icmp_seq=3 Destination Host Unreachable
From 192.168.1.67 icmp_seq=4 Destination Host Unreachable

```and so on.

Thanks!

---

### Post by ratdog on 2011-03-21
In Windows, 192.168.1.67 is listed as the IPv4 address.

---

### Post by conneco on 2011-03-21
> **ratdog said:**
> Here is the output of the ping:

```
@ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.67 icmp_seq=2 Destination Host Unreachable
From 192.168.1.67 icmp_seq=3 Destination Host Unreachable
From 192.168.1.67 icmp_seq=4 Destination Host Unreachable

```and so on.

Thanks!

do you know the ip of your router did you try 192.168.1.254?

Can you post the output of

sudo dhclient3 eth0

---

### Post by ratdog on 2011-03-21
pinging 192.168.1.254 did get a response.

Here is the output:

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:23:5a:d2:1f:13
Sending on   LPF/eth0/00:23:5a:d2:1f:13
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.67 from 192.168.1.254
DHCPREQUEST of 192.168.1.67 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.67 from 192.168.1.254
bound to 192.168.1.67 -- renewal in 40074 seconds.
```

Thanks

---

### Post by conneco on 2011-03-21
Yeah it looks like the networking is up as far as I can see what's the issue can you not get Internet?

---

### Post by ratdog on 2011-03-21
When I turn off wireless, network manager does not detect the wired connection.  I have a wired network setup, but it does not show that it connects.  

I just noticed that when I click on the network manager icon in the panel, there is no device shown under 'Wired Networks'.  

It just says 'device not managed'.

---

### Post by ratdog on 2011-03-22
Anyone have an idea to get network manager to recognize my wired connection?

---

### Post by ratdog on 2011-04-01
Is there another network connection app I should try?

---

### Post by dineshs on 2011-04-02
>  In Network Connections there is no Auto eth0 listing and when I create a wired connection, as soon as I enter details, the 'Apply' button grays out! Am I missing some permissions?
After typing IP address,mask and gateway [COLOR="Red"]hit enter[/COLOR]
Then give DNS and apply
If there is no luck run ```
sudo gedit /etc/network/interfaces
```and ensure that the file reads only```
auto lo
iface lo inet loopback
``` comment out (put a [COLOR="Red"]#[/COLOR] before )all other lines (You may delete all other lines but save a copy before doing that)
Restart and see

---

### Post by walt.smith1960 on 2011-04-02
> **ratdog said:**
> Hello,
<snip>
lspci
```
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
**08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)**
```Thanks for you help!

Broadcom strikes again, this time ethernet?  (Broadcom wireless chips seem to be frequent problems) Is there anything in System -> Administration -> Hardware Drivers/Additional Drivers?

---

### Post by ratdog on 2011-04-02
Thank You dineshs!

My /etc/network/interfaces read like this:
```
auto lo

iface lo inet loopback

iface eth0 inet dhcp

auto eth0
``` 

I commented out the last 2 lines and after reboot, the ethernet connection worked!

Now I can backup to my NAS without it taking days.:)

---

