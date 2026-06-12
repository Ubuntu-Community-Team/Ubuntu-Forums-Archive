---
title: "How to configure network with adsl modem that got no password"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by madone1 on 2009-04-13
I have new Internet provider ho gave me adsl modem Scientific Atlanta EPC 2203(before i had adsl modem/router and everything worked perfect). This modem goes directly to Internet and i don't have to enter user name and password(didn't even get one from ISP). When i first booted my comp with this modem the Internet speed was terrible slow. Then i figured if i do 
"sudo /etc/init.d/networking restart" that my connection works like dream.
Now i have to "sudo /etc/init.d/networking restart" every time i restart X or boot PC. I dont now how to solve this  pleas help. I have tried even to configure pppoeconf but it didnt work because i have to enter user name and pass.

This is output that i get when i restart network
```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                  There is already a pid file /var/run/dhclient.eth0.pid with pid 12616
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:4d:9a:7d:68
Sending on   LPF/eth0/00:1a:4d:9a:7d:68
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 83.139.64.22 port 67
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:4d:9a:7d:68
Sending on   LPF/eth0/00:1a:4d:9a:7d:68
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 88.207.31.186 from 88.207.28.1
DHCPREQUEST of 88.207.31.186 on eth0 to 255.255.255.255 port 67
DHCPACK of 88.207.31.186 from 88.207.28.1
bound to 88.207.31.186 -- renewal in 69052 seconds.
 * Stopping NTP server ntpd
   ...done.


```

my interfaces file (tried with various settings)
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0
```

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
address 00:1a:4d:9a:7d:68
netmask 255.255.255.255
gateway 88.207.28.1

auto eth0

```

ifconfig
```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9a:7d:68  
          inet addr:88.207.31.186  Bcast:255.255.255.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:16999775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13893646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5721321129 (5.7 GB)  TX bytes:3409021903 (3.4 GB)
          Interrupt:23 Base address:0x6000 
 
```

```
~$ /sbin/route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
88.207.28.0     *               255.255.252.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         88.207.28.1     0.0.0.0         UG    100    0        0 eth0

```

~$ sudo gedit /etc/resolv.conf
```
domain domain.com
nameserver 213.149.32.23
nameserver 83.139.64.10
```

P.S. My Network Manager don t work after i did install Virtual Box?(i doubt that this is connected in any whey with my problem)
So every thing i do is from the terminal

---

### Post by chili555 on 2009-04-13
> My Network Manager don t workIt will not work as long as you are managing your interface with your */etc/network/interfaces* file. As a matter of fact, if your computer is a desktop model that stays at home and is always tethered to the ADSL modem, you really don't even need Network Manager and can safely uninstall it.

The next time you boot, before you restart networking, please run:```
sudo ethtool eth0
```Then restart networking and run the command again. Let us compare the settings and try to figure out how to fix it.

---

### Post by madone1 on 2009-04-13
Thank you for replay and advice regarding Network manager it is history from now. I assumed that Network manager saves configuration in interfaces file, and yes my pc is desktop. 

"sudo ethtool eth0" before i restarted networking 
```
 
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```

and after the networking restart

```
 
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```
I don t see any difference between two outputs of "sudo ethtool eth0"

---

### Post by superprash2003 on 2009-04-13
you dont need to use pppoeconf  i think... you seem to be getting an ip addresss.. arent you able to access the internet?

---

### Post by madone1 on 2009-04-13
I can access network when i do "sudo /etc/init.d/networking restart" but when i boot my pc or restart x something isn't right because internet is so slow that is unusable, even Pidgin can t connect to gmail accounts.
I sometimes get this output when i tray "sudo /etc/init.d/networking restart" and my internet connection is unbelievingly  slow
```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 7823
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:4d:9a:7d:68
Sending on   LPF/eth0/00:1a:4d:9a:7d:68
Sending on   Socket/fallback
DHCPREQUEST of 88.207.29.163 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 88.207.29.163 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 88.207.29.163
PING 88.207.28.1 (88.207.28.1) 56(84) bytes of data.

--- 88.207.28.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 25.883/25.883/25.883/0.000 ms
bound: renewal in 21607 seconds.
```

---

### Post by superprash2003 on 2009-04-14
your MTU value is 576 which is pretty low.. you may want to try changing that .. [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by madone1 on 2009-04-15
I did change MTU but it made no diference. Now my internet connection works after restart and MTU value is still 576. Sometimes after  "sudo /etc/init.d/networking restart" i get ```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 7823
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:4d:9a:7d:68
Sending on   LPF/eth0/00:1a:4d:9a:7d:68
Sending on   Socket/fallback
DHCPREQUEST of 88.207.29.163 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 88.207.29.163 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 88.207.29.163
PING 88.207.28.1 (88.207.28.1) 56(84) bytes of data.

--- 88.207.28.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 25.883/25.883/25.883/0.000 ms
bound: renewal in 21607 seconds.
``` 
you can see in the and "No DHCPOFFERS received". When i get this output network isn't working.

---

### Post by superprash2003 on 2009-04-16
in your first post you have listed various /etc/network/interfaces outputs.. which one are you using now? how many pcs do you have in your network?>

---

### Post by madone1 on 2009-04-17
I gave up from configuring network in "interfaces" file. And installed Network Manager, but i now have similar problem. Network Manager configured  "Wired connection 1" and "Auto eth0", but on the boot of PC NM chose  "Auto eth0" that don t work and i have too manual chose "Wired connection 1" that works. Now my "/etc/network/interfaces" file looks like this ```
auto lo
iface lo inet loopback
```

---

### Post by superprash2003 on 2009-04-17
add these lines

iface eth0 inet dhcp

auto eth0

---

