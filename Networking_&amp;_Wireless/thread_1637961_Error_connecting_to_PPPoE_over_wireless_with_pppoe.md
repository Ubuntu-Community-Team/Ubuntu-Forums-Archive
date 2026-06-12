---
title: "Error connecting to PPPoE over wireless with pppoeconf"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by whatev on 2010-12-05
Hi all,



I am trying to connect a computer running Ubuntu 10.04 LTS to the internet via PPPoE over WLAN and having trouble connecting.

The device that connects to WAN is a D-Link DSL-G604T. WAN connection in this device is configured for bridged mode.

This is what I have done:

"ifconfig wlan0"

> wlan0 Link encap:Ethernet HWaddr 00:0f:3d:af:19:de 
inet addr:10.1.1.2 Bcast:10.255.255.255 Mask:255.0.0.0
inet6 addr: fe80::20f:3dff:feaf:19de/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:6309 (6.3 KB)

"sudo pppoeconf wlan0"

> pppoeconf found 1 ethernet device: wlan0

pppoeconf will configure /etc/ppp/peers/dsl-provider: Yes

pppoeconf will change configuration 'noauth' + 'defaultroute' and remove 'nodetach' where neccessary: Yes

Input username for PPP login: Done

Input password for PPP login: Done

pppoeconf will add nameservers provided by ISP to /etc/resolv.conf: Yes

pppoeconf will clamp MSS at 1452 bytes: Yes

PPPD will start at boot time? No

pppoeconf will now start connection: Yes

pppoeconf states the DSL connection has been triggered and that I can use 'plog' command to see the status or 'ifconfig ppp0' for general interface info.

"plog"

> Dec 5 19:17:53 mum-desktop pppd[1702]: Plugin rp-pppoe.so loaded.
Dec 5 19:17:53 mum-desktop pppd[1702]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Dec 5 19:17:53 mum-desktop pppd[1704]: pppd 2.4.5 started by root, uid 0
Dec 5 19:18:28 mum-desktop pppd[1704]: Timeout waiting for PADS packets
Dec 5 19:18:28 mum-desktop pppd[1704]: Unable to complete PPPoE Discovery

"ifconfig ppp0"

> ppp0: error fetching interface information: Device not found

I now restart and find NetworkManager-applet not registering any connections because they have been manually configured. This is now the contents of "/etc/network/interfaces":

> auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider

auto wlan0
iface wlan0 inet manual

"sudo pon dsl-provider"

> Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

"plog"

> Dec 5 19:24:20 mum-desktop pppd[1295]: Timeout waiting for PADO packets
Dec 5 19:24:20 mum-desktop pppd[1295]: Unable to complete PPPoE Discovery
Dec 5 19:24:50 mum-desktop pppd[1295]: error sending pppoe packet: Network is down
Dec 5 19:24:50 mum-desktop pppd[1295]: error receiving pppoe packet: Network is down
Dec 5 19:24:55 mum-desktop pppd[1295]: error sending pppoe packet: Network is down

"ipconfig ppp0"

> ppp0: error fetching interface information: Device not found

"ipconfig wlan0"

> wlan0 Link encap:Ethernet HWaddr 00:0f:3d:af:19:de 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


It now seems that the wireless connection is not being made to the DSL-G604T, which would explain why PPPoE cannot connect.

Does anyone know what I could do to get the computer connected to the internet?

---

### Post by dineshs on 2010-12-05
Please try this
Edit the file */etc/network/interfaces*```
gksudo gedit /etc/network/interfaces
```
so that it contains only these two lines
```
auto lo
iface lo inet loopback

```
restart PC(your NM icon will be back)
Connect using pon dsl-provider and see if it works.If not please post the result of```
ping 4.2.2.1 -c5
```and ```
cat /etc/resolv.conf
```

---

### Post by mcfly2309 on 2011-01-24
hello, i have the same problem in mint debian (should be the same) and i followed all the instructions, so i'll post them here, to see if you can help...

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# allow-hotplug eth0
# NetworkManager#iface eth0 inet dhcp

# iface dsl-provider inet ppp
# pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
# provider dsl-provider

# auto wlan0
# iface wlan0 inet manual

# auto eth1
# iface eth1 inet manual

# iface dsl-provider inet ppp
# provider dsl-provider

# auto eth1
# iface eth1 inet manual

# iface dsl-provider inet ppp
# provider dsl-provider

# auto wlan0
# iface wlan0 inet manual
```

i've commented the lines each time i have run pppoeconf again and again...

```
alex@alex-lmde ~ $ sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1e:ec:3c:4f:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2720 (2.6 KiB)  TX bytes:2720 (2.6 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:190.95.50.194  P-t-P:192.168.216.66  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:596 (596.0 B)  TX bytes:54 (54.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:10:00:bf  
          inet addr:192.168.1.7  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::221:63ff:fe10:bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13882 (13.5 KiB)  TX bytes:22961 (22.4 KiB)
```

this is after i connect to wireless and then do "pon dsl-provider"

```
alex@alex-lmde ~ $ sudo plog
Jan 25 13:09:54 alex-lmde pppd[2047]: CHAP authentication succeeded: CHAP authentication success, unit 7780
Jan 25 13:09:54 alex-lmde pppd[2047]: CHAP authentication succeeded
Jan 25 13:09:54 alex-lmde pppd[2047]: peer from calling number 00:30:88:02:21:C9 authorized
Jan 25 13:09:54 alex-lmde pppd[2047]: not replacing existing default route via 192.168.1.254
Jan 25 13:09:54 alex-lmde pppd[2047]: local  IP address 190.95.50.194
Jan 25 13:09:54 alex-lmde pppd[2047]: remote IP address 192.168.216.66
Jan 25 13:09:54 alex-lmde pppd[2047]: primary   DNS address 200.75.0.4
Jan 25 13:09:54 alex-lmde pppd[2047]: secondary DNS address 216.155.73.40
```

```
alex@alex-lmde ~ $ ping 4.2.2.1 -c5
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.

--- 4.2.2.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4031ms
```

i can connect to my wireless modem, but pages don't load...

---

### Post by dineshs on 2011-01-25
> i've commented the lines each time i have run pppoeconf again and again...You need not run pppoeconf again and again.Run once then edit the file so that it contains only those 2 lines.
run sudo pon dsl-provider and connect
Post the result of ```
route -n
```

---

