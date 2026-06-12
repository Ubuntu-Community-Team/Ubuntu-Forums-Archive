---
title: "Problem with Broadcom BCM4312 sharing Access Point for Android phone"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by nipunshakya on 2012-08-12
Workstation: Ubuntu 12.04 Desktop on Dell Inspiron 1440.

Hello all. Since couple of days, i am trying to use my laptop as an AP so that my new android phone can connect to it. I have a Broadcom BCM4312 router with ethernet connection for internet access.
So i used [http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd) and [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) to let my router use the b43 firmware and use the hostapd.
I have installed b43 firmware via ```
sudo apt-get install firmware-b43-lpphy-installer
``` and successfully have made the Access Point which is excellently scanned by the phone that will be using the internet if i succeed.
I followed the instructions from the following link :
[http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/](http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/) to make the Access Point.

However, at the 'Final Steps' heading of the link that i used to make the Access Point, i don't think the bash script is working well with me. i get the following output if i run that script:
```

winuxuser@MagicBox:~$ sudo ./initSoftAP wlan0 eth0
Internet Systems Consortium DHCP Server 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Wrote 0 leases to leases file.
net.ipv4.ip_forward = 1

No subnet declaration for wlan0 (no IPv4 addresses).
** Ignoring requests on wlan0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface wlan0 is attached. **


Not configured to listen on any interfaces!
l2_packet_receive - recvfrom: Network is down


```
 and the cursor keeps blinking and blinking like forever.Strange thing is that after the execution of the script, i am totally disconnected even from ethernet connected internet and have to make a restart again.

So my question is, what is missing in my steps that i cannot forward the data packets from my laptop to the phone? 
my phone can clearly see the network, and it keeps on saying 'Obtaining ip address' and after some time, gets disconnected and the process to obtain the ip remains forever incomplete... 

any suggestions gurus?


```

winuxuser@MagicBox:~$ sudo lspci -vvn |grep 43 -A7
0c:00.0 0280: 14e4:4315 (rev 01)
	Subsystem: 1028:000c
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f6cfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
--
	Kernel driver in use: b43-pci-bridge
	Kernel modules: wl, ssb

winuxuser@MagicBox:~$ 

```

```

winuxuser@MagicBox:~$ sudo ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:26:5e:54:e8:eb  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:25:64:55:9e:9d  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe55:9e9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2927552 (2.9 MB)  TX bytes:591038 (591.0 KB)
          Interrupt:46 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178089 (178.0 KB)  TX bytes:178089 (178.0 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr 00-26-5E-54-E8-EB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:714339 (714.3 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:54:e8:eb  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe54:e8eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16790 (16.7 KB)  TX bytes:66780 (66.7 KB)

```

```

winuxuser@MagicBox:~$ lspci -k | grep -A 3 -i "network"
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card
	Kernel driver in use: b43-pci-bridge
	Kernel modules: wl, ssb
winuxuser@MagicBox:~$ 

```

I have completely switched to ubuntu and i don't want to go back to windows to use Connectify for the connections for my phone... i hope someone could help me out with the problem.... thank you for your support.. :)

---

### Post by nipunshakya on 2012-08-13
one more thing to add... before executing the script initSoftAP, the execution of ```
sudo hostapd /etc/hostapd/hostapd.conf
``` would result my phone trying to obtain the ip continuously without any luck, but now, after the execution of the initSoftAP, i would get the following:

```
winuxuser@MagicBox:~$ sudo hostapd /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
Using interface wlan0 with hwaddr 00:26:5e:54:e8:eb and ssid 'The_G_Spot'
wlan0: STA 3e:19:be:1f:ab:b8 IEEE 802.11: disassociated
l2_packet_receive - recvfrom: Network is down
wlan0: IEEE 802.11 disassociated
winuxuser@MagicBox:~$ 

```

I have become clueless about what should i do now ... :(

---

### Post by nipunshakya on 2012-08-20
I think my problem will never be solved now.. :(

---

### Post by nipunshakya on 2012-08-25
Bump...

---

### Post by nipunshakya on 2012-08-25
Could anyone atleast explain me what the following lines mean?? how do i make the script get correct interface address for 'mon.wlan1' ...??? :(
```
nipun@MagicBox:~$ sudo ./initSoftAP wlan1 eth0
Internet Systems Consortium DHCP Server 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Wrote 0 leases to leases file.
net.ipv4.ip_forward = 1
Error getting interface address for 'mon.wlan1'; No such device
Error getting interface information.


```

---

