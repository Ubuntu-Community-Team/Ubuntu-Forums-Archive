---
title: "Problem with wired network connection"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by sokolovic on 2010-08-27
Hello there! 

I have just installed Ubuntu 10.04, and I have a problem with connecting via wired connection. I didn't have such a problems with previous versions of Ubuntu.

When I plug in a network cable, it's like trying to establish a connection, and after few seconds I get a message that I am disconnected from network. 

Hope someone had similar issue, any help would be good.
Btw, it's eMachines e720 laptop, if it does matter...

Cheers!
sokolovic

---

### Post by Iowan on 2010-08-27
From a terminal (Applications>Accessories>Terminal), try **sudo dhclient** Your results will *probably* end with something like: ```
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by sokolovic on 2010-08-27
Here is the result of **sudo dhclient:**

```

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/wlan0/00:24:2b:75:b6:4a
Sending on   LPF/wlan0/00:24:2b:75:b6:4a
Listening on LPF/eth0/00:23:5a:53:10:9b
Sending on   LPF/eth0/00:23:5a:53:10:9b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
receive_packet failed on wlan0: Network is down
DHCPOFFER of 192.168.40.7 from 192.168.40.1
DHCPREQUEST of 192.168.40.7 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.40.7 from 192.168.40.1
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.40.7 -- renewal in 116006 seconds.


```

---

### Post by Iowan on 2010-08-27
Hmmm... :-k
Occasionally, the results come back different than expected.
That's OK! The machine seems to get an IP address, but it's quite curious that */etc/resolv.conf* is missing - and why. You might try repeating the exercise after (again from a terminal) **sudo touch /etc/resolv.conf**

---

### Post by sokolovic on 2010-08-27
Here it is:

```

sokolovic@sokolovic-laptop:~$ sudo touch /etc/resolv.conf
[sudo] password for sokolovic: 
sokolovic@sokolovic-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/wlan0/00:24:2b:75:b6:4a
Sending on   LPF/wlan0/00:24:2b:75:b6:4a
Listening on LPF/eth0/00:23:5a:53:10:9b
Sending on   LPF/eth0/00:23:5a:53:10:9b
Sending on   Socket/fallback
DHCPREQUEST of 192.168.40.7 on eth0 to 255.255.255.255 port 67
receive_packet failed on wlan0: Network is down
DHCPACK of 192.168.40.7 from 192.168.40.1
bound to 192.168.40.7 -- renewal in 110679 seconds.

```

Still, when I connect network cable, i get message: Disconnected - You are not offline.

---

### Post by Iowan on 2010-08-27
:( I must be missing something else (another missing file?)...
In the meantime, does **ifconfig -a** show an interface with that (192.168.40.7) address?

---

### Post by sokolovic on 2010-08-27
Here is new result:

```

sokolovic@sokolovic-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:5a:53:10:9b  
          inet6 addr: fe80::223:5aff:fe53:109b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:402 (402.0 B)  TX bytes:1152 (1.1 KB)
          Interrupt:27 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:75:b6:4a  
          inet6 addr: fe80::224:2bff:fe75:b64a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

It's a fresh install, i don't know what's wrong...

---

### Post by fx_viallon on 2010-10-04
Hi!

i have a different issue, but tried the hints given in this post. My problem is also that i cannot connect with the ethernet card to the home network, nor even ping the router, while the wireless one works fine. 
The LEDs on the network hub blink every two seconds, not as for normal working connections where they are static or blinking fastly when there is traffic.
I tried to connect with another network cable, but it didn' help. I also tried to configure the IP, gateway and DNS manually but it didn't worked out either.

Here are the results of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:24:7e:6e:23:c5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124490 (124.4 KB)  TX bytes:124490 (124.4 KB)

pan0      Link encap:Ethernet  HWaddr 4a:48:19:47:46:9c  
          inet6 addr: fe80::4848:19ff:fe47:469c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:13058 (13.0 KB)

usb0      Link encap:Ethernet  HWaddr 02:80:37:ec:02:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:63:21:7a  
          inet6 addr: fe80::221:6aff:fe63:217a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3193645 (3.1 MB)  TX bytes:811051 (811.0 KB)

and here of dhclient with wlan working :

Listening on LPF/usb0/02:80:37:ec:02:00
Sending on   LPF/usb0/02:80:37:ec:02:00
Listening on LPF/pan0/4a:48:19:47:46:9c
Sending on   LPF/pan0/4a:48:19:47:46:9c
Listening on LPF/eth0/00:24:7e:6e:23:c5
Sending on   LPF/eth0/00:24:7e:6e:23:c5
Listening on LPF/wlan0/00:21:6a:63:21:7a
Sending on   LPF/wlan0/00:21:6a:63:21:7a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPREQUEST of 192.168.1.28 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.28 from 192.168.1.1
bound to 192.168.1.28 -- renewal in 2147483648 seconds.

and here when i disalble the wireless lan:

fix@fix-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/usb0/02:80:37:ec:02:00
Sending on   LPF/usb0/02:80:37:ec:02:00
Listening on LPF/pan0/4a:48:19:47:46:9c
Sending on   LPF/pan0/4a:48:19:47:46:9c
Listening on LPF/wlan0/00:21:6a:63:21:7a
Sending on   LPF/wlan0/00:21:6a:63:21:7a
Listening on LPF/eth0/00:24:7e:6e:23:c5
Sending on   LPF/eth0/00:24:7e:6e:23:c5
Sending on   Socket/fallback
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST of 192.168.1.28 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST of 192.168.1.28 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
^C

Some information about the network card i retrieved with the command "lshw":
  *-network
             description: Ethernet interface
             product: 82567LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:24:7e:6e:23:c5
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.8-3 latency=0 multicast=yes
             resources: irq:28 memory:f2600000-f261ffff memory:f2625000-f2625fff

Any help is appreciated.
Thanks.

---

