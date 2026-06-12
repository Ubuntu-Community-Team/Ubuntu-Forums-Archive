---
title: "Cannot obtain IP address on wired connection, redux"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by jgb2185 on 2010-03-12
The [IP address acquisition problem I reported earlier]("http://ubuntuforums.org/showthread.php?t=1394320") has returned, and I am stymied.

To recap: Ubuntu 9.10 would not obtain an IP address via a wired Ethernet connection. I resolved the problem at the time by configuring eth0 in **[FONT="Courier New"]/etc/network/interfaces[/FONT]**:

```

auto eth0
iface eth0 inet dhcp

```

and disabling Network Manager in **Preferences** > **Startup Applications**.

After a powering down the PC today, the problem has returned. It appears that **[FONT="Courier New"]dhclient[/FONT]** cannot obtain an IP address. This is true whether I am connected to the router (a Linksys WRT54G running Tomato), or directly to the DSL modem. When my usually wireless Ubuntu 9.10 laptop is wired to the router, it obtains an address almost instantly.

I have made no changes to the network configuration since January. I have tried to keep current on Ubuntu updates.

I have appended below several diagnostic items that may be useful. I am perplexed by this issue, and would appreciate any suggestions for further troubleshooting.

Thanks...

JGB


```

jgb@alienware:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:30:1b:ac:5b:9e  
          inet6 addr: fe80::230:1bff:feac:5b9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc000 


jgb@alienware:~$ sudo lspci|grep Eth
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


jgb@alienware:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp


jgb@alienware:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: off
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes


jgb@alienware:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 3351
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:1b:ac:5b:9e
Sending on   LPF/eth0/00:30:1b:ac:5b:9e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:1b:ac:5b:9e
Sending on   LPF/eth0/00:30:1b:ac:5b:9e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Iowan on 2010-03-13
I doubt [this]("http://ubuntuforums.org/showthread.php?t=1156441") one will help, but you can try... I've seen other threads that suggest NM may need to be completely removed (purged).

---

### Post by hfxrzw on 2010-03-13
Be very careful!! I did the same (removing NM) and then off course you haven't got a network connection any more to update or reinstall it. I just ended up re-installing Ubuntu completely, with loss of everything.

---

### Post by jgb2185 on 2010-03-13
I thank Iowan and hfxrzw for their responses. I had removed "option rfc3442" from [FONT="Courier New"]**/etc/dhcp3/dhclient.conf**[/FONT] during my last struggle with this issue, in January. My current [FONT="Courier New"]**dhclient.conf**[/FONT] file is attached to this post. I have not yet uninstalled **network-manager**.

Here's what else I've tried since my last post.

1) Tried removing the **8139cp** driver  --  no joy.

```

 $ sudo lsmod | grep 813
 
 8139too    22620  0
 8139cp     19260  0
 mii         5212  2  8139too,8139cp
 
 $ sudo rmmod -f 8139cp
 $ lsmod | grep 813
 
 8139too    22620  0
 mii         5212  2  8139too
 
 $ sudo dhclient eth0
 
 There is already a pid file /var/run/dhclient.pid with pid 2308
 killed old client process, removed PID file
 Internet Systems Consortium DHCP Client V3.1.2
 Copyright 2004-2008 Internet Systems Consortium.
 All rights reserved.
 For info, please visit http://www.isc.org/sw/dhcp/
 
 Listening on LPF/eth0/00:30:1b:ac:5b:9e
 Sending on   LPF/eth0/00:30:1b:ac:5b:9e
 Sending on   Socket/fallback
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
 No DHCPOFFERS received.
 No working leases in persistent database - sleeping.

```

2) Tried removing the **8139too** driver; no joy.

```

 $ sudo modprobe 8139cp
 $ sudo rmmod -f 8139too
 $ lsmod | grep 813
 
 8139cp     19260  0
 mii         5212  2  8139cp
 
 $ sudo dhclient eth0
 
 There is already a pid file /var/run/dhclient.pid with pid 3251
 killed old client process, removed PID file
 Internet Systems Consortium DHCP Client V3.1.2
 Copyright 2004-2008 Internet Systems Consortium.
 All rights reserved.
 For info, please visit http://www.isc.org/sw/dhcp/
 
 SIOCSIFADDR: No such device
 eth0: ERROR while getting interface flags: No such device
 eth0: ERROR while getting interface flags: No such device
 Bind socket to interface: No such device

```

3) Just to be safe, rebooted and tried removing the **8139too** driver again; same results.

4) Tried the cable unplug-reconnect trick mentioned in some forum threads  --  no joy.

5) Tried a different cable on a different router port  --  no joy.

6) Disabled **Bluetooth Manager** under **System** > **Preferences**, then rebooted  --  no joy.

My next steps will be:

7) Try the several kernel boot parameters listed in [this thread]("http://ubuntuforums.org/showthread.php?t=411324") and [this thread]("http://ubuntuforums.org/showthread.php?t=274764").

8) Try booting from an earlier kernel.

9) Uninstall network-manager.

10) Carefully compare the configurations of my desktop PC and my laptop. Both use the Realtek 8139 C chipset, but while the desktop is having this issue, the laptop has no problem whatsoever in establishing a wired IP connection.

11) Try to set up a working static IP, first from the live CD and then from my current Ubuntu install.

As always, any comments or suggestions are welcome.

Thanks...

JGB

---

### Post by Iowan on 2010-03-14
> **hfxrzw said:**
> Be very careful!! I did the same (removing NM) and then off course you haven't got a network connection any more to update or reinstall it. I just ended up re-installing Ubuntu completely, with loss of everything.I hesitate to suggest removing NM for the same reason...

---

