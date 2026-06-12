---
title: "Ubuntu ARP failure to respond for TFTP"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by Aeneas32 on 2010-11-18
I am finding that my Ubuntu running under Windows Vista/Virtualbox has suddenly stopped TFTP server-ing of images to an external U-Boot/Linux board, a few days after the latest Virtualbox upgrade. It was working for a month, up until 2 days ago.
Viewing the Wireshark output on the Windows Vista host, I can see the external board request the ARP request:
=============================================
1 0.000000 ApproTec_a0:02:b5 Broadcast ARP Who has 192.162.0.19? Tell 192.168.0.14
=============================================
but no response is sent back to the requesting board from Ubuntu, 
which is assigned 192.168.0.19 by the cable modem/dhcp server.
 
Observations: 
1) the Ubuntu Internet Browser can browse the web.
 
2) Running Wireshark on the Ubuntu results in the application failing to Start Capture, because it sees No interfaces.
The Windows Host is at 192.168.0.18 .
 
3) Virtualbox was configured as a Bridged Adapter prior to Virtualbox upgrade, and still shows that setting in Devices/Network Settings.
 
What could cause Ubuntu to fail to respond to ARP requests ?
---------------------------------------------------------------------------------
 
The ifconfig for the guest Ubuntu is:
=============================================================================
eth0 Link encap:Ethernet HWaddr 08:00:27:82:8a:a7 
inet addr:192.168.0.19 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::a00:27ff:fe82:8aa7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:126761 errors:0 dropped:0 overruns:0 frame:0
TX packets:95883 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:38298823 (38.2 MB) TX bytes:49928924 (49.9 MB)
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:112 errors:0 dropped:0 overruns:0 frame:0
TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:9384 (9.3 KB) TX bytes:9384 (9.3 KB)
==================================================================================
 
$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
==================================================================================

---

