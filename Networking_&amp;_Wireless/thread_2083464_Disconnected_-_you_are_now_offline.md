---
title: "Disconnected - you are now offline"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by ImTheBatman on 2012-11-12
Hello, I have been using Ubuntu 12.04 for a few months now and everything has been working great, but suddenly yesterday i turned on my computer and I get this message in regards to my wired network connection. If I try to reconnect, the network icon in unity taskbar does the "connecting" animation for a few minutes and then again throws the diconnected - you are now offline message.

I am using a broadband connection and am connected directly to the modem with no router in the middle, my connection also does not require authentication\dialing or a static IP. When I installed ubuntu 12.04 in the first place I did not need to configure anything, networking just worked out of the box. My internet still works perfectly fine under the Windows 7 installation on the very same computer.

ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:37:5d:aa  
          inet6 addr: fe80::1e6f:65ff:fe37:5daa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:433896 (433.8 KB)  TX bytes:17159 (17.1 KB)
          Interrupt:53 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28608 (28.6 KB)  TX bytes:28608 (28.6 KB)


```

---

### Post by ImTheBatman on 2012-11-12
Okay... I  have reconfigured the network connection to use a static ipv4 instead of trying to do DHCP. I set in the IP, mask and gateway Windows got from the DHCP and it's working. So apparently the problem is in dhcp. the command dhclient just exits, when I use "dhclient -v" I get:

```
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

can't create /var/lib/dhcp/dhclient.leases: Permission denied
No broadcast interfaces found - exiting.

```

So I assume you need root for dhclient, the second error is weird though because ifconfig shows eth0 as BROADCAST. So I use "sudo dhclient -v eth0" and get:
```
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/1c:6f:65:37:5d:aa
Sending on   LPF/eth0/1c:6f:65:37:5d:aa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15

```

and so DHCPDISCOVER continues listening and gets nothing. Is this a bug in dhclient or am I doing something wrong here?

---

### Post by ImTheBatman on 2012-11-12
Come on guys, a hundred views and no help? There must be someone here who knows how to work things in Ubuntu. I've been debugging this issue for hours alone now...

---

### Post by ImTheBatman on 2012-11-12
solved it myself, whatever, at least i learned a couple of things about linux

---

