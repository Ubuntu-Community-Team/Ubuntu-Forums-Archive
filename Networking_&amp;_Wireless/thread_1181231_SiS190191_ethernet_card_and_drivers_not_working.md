---
title: "SiS190/191 ethernet card and drivers not working"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by Get_It on 2009-06-07
Hi there,
I just got a INSYS GameForce HD 9761 Linux through the Portuguese "*E-Escolas*" program which came with the *Caixa Mágica* distribution and is equipped with a SiS191 Gigabit Ethernet Adapter. Well, I immediately installed instead Windows XP and the recently released Ubuntu 9.04 on it -- I use Ubuntu 8.10 on my desktop for less than a year now.

The installation went great, I chose the partitions, gave the basic information that was requested and it was done. However, when I logged in on Ubuntu and wanted to check for updates and install new software the problems started. I simply couldn't get the laptop to connect to my Touchstone cable modem through a wired connection.

```
Linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
``````
$ lspci -v
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
    Subsystem: CLEVO/KAPOK Computer Device 0802
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at d3307000 (32-bit, non-prefetchable) [size=128]
    I/O ports at 1000 [size=128]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: sis190
    Kernel modules: sis190

``````
$ sudo modprobe -l | grep sis190
kernel/drivers/net/sis190.ko
``````
$ dmesg | grep sis
[    0.856392] mtrr: your CPUs had inconsistent variable MTRR settings
[    1.749676] sata_sis 0000:00:05.0: version 1.0
[    1.749698] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.749703] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.749839] scsi0 : sata_sis
[    1.749940] scsi1 : sata_sis
[    2.220903] pata_sis 0000:00:02.5: version 0.5.2
[    2.220917] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.221025] scsi2 : pata_sis
[    2.221086] scsi3 : pata_sis
[    7.906290] sis190 Gigabit Ethernet driver 1.2 loaded.
[    7.906319] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    7.906334] sis190 0000:00:04.0: setting latency timer to 64
```Network Manager is not helping much, yet the "Auto eth0" network is active and eth0 is able to return an IP address from my ISP's DHCP. However, it still is unable to connect to any host nor ping my ISP's IP address.

**[COLOR=Red] EDIT:[/COLOR]** I also tried editing /etc/network/interfaces and /etc/resolv.conf, but to no use.

I tried to check the network/Internet connection on Windows XP and after installing the drivers from the driver's CD that came with the laptop it worked well. I then tried to check the drivers for Linux. It was then I came upon the [SiS190 ethernet drivers topic]("http://ubuntuforums.org/showthread.php?t=335461"), which dates back to 2007, and while the drivers on the manufacturers website don't work the drivers on the Linux kernel seem to have been fixed.

Meanwhile, I was able to get the Wireless connection going and at a first look it doesn't seem to have any problems.

FYI: Before formatting and installing Ubuntu I didn't check to see if the ethernet adapter worked on *Caixa Mágica* :oops: And while the computer came with a Linux distribution installed and with a CD of the OS, the CD with the drivers, which also came with the laptop, only has them for Windows XP and Vista.

Any help with this would be appreciated.
Thank you very much,

---

### Post by coffeeaddict22 on 2009-06-07
Hi,
What's the output of ```
lshw -C network
nm-tool
route -n
ifconfig
```
Should be more than enough to start with :-)

---

### Post by Get_It on 2009-06-08
Hi,
Thank you for replying.

Here are the outputs:
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:8e:5e:19
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=88.157.140.190 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:43:8e:ed:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:b2:36:48:c0:a9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

``````
$ nm -tool
nm: 'a.out': No such file

``````
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
88.157.140.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         88.157.140.254  0.0.0.0         UG    0      0        0 eth0

``````
$ ifconfig
eth0      Link encap:Ethernet
          inet addr:88.157.140.190  Bcast:88.157.140.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:dc8a:5e19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50660 (50.6 KB)  TX bytes:9175 (9.1 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4908 (4.9 KB)  TX bytes:4908 (4.9 KB)

wlan0     Link encap:Ethernet
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```Thank you,

---

### Post by Crafty Kisses on 2009-06-08
Now you've said you can't ping your ISP, but I just want to double check. So let's see if you can ping any websites and actually receive a reply from that website. If you get some replies, I might have an idea on what the actual issue is. So first open up a Terminal and run the following:
```
ping google.com
```
See if you get any replies from Google it might be a DNS problem. Now looking at the results of your routing table it looks good, nothing looks out of place. The second thing I want you to do is try opening Firefox or whatever browser you may use, then type this in at the navigation bar:
```
74.125.45.100
```
That should in theory if it's a DNS issue connect you to Google. I'd also like to see a couple more things. Open up another Terminal after you're doing the things I've stated, and then run:
```
cat /etc/resolv.conf
```
Just post what's in that document here on the forums and from there I or somebody else can help you further.

---

### Post by Get_It on 2009-06-08
Hello,

```
$ ping google.com
ping: unknown host google.com

```Firefox is also unable to "establish a connection to the server at 74.125.45.100"

```
$ cat /etc/resolv.conf 
# Generated by NetworkManager
domain tvtel.pt
search tvtel.pt
nameserver 88.157.32.12
nameserver 88.157.32.77

```I appreciate all the help.

---

### Post by chili555 on 2009-06-09
Ahhh! My favorite kind of problem: everything looks perfect except it just doesn't work. First of all, the command is:```
nm-tool
```It is not nm  -tool, as you seem to have typed. Next, let's try to see if the driver or Network Manager is the problem. First, we'll be sure the wireless is shut down:```
sudo ifconfig wlan0 down
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 up
sudo dhclient eth0
ping -c3 www.google.com
```

---

### Post by Get_It on 2009-06-10
Well, here we go:

```
$ nm-tool 

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sis190
  State:             connected
  Default:           yes

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         88.157.141.137
    Prefix:          24 (255.255.255.0)
    Gateway:         88.157.141.254

    DNS:             88.157.32.12
    DNS:             88.157.32.77


- Device: wlan0 -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connecting (configuring)
  Default:           no

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    goda:            Infra, 00:1C:F0:F5:1C:C4, Freq 2442 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2

``````
$ sudo ifconfig wlan0 down
$ sudo /etc/init.d/NetworkManager stop
 * Stopping network connection manager NetworkManager                    [ OK ] 
$ sudo ifconfig eth0 up
$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:90:f5:8e:5e:19
Sending on   LPF/eth0/00:90:f5:8e:5e:19
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 88.157.141.175 from 10.5.0.1
DHCPREQUEST of 88.157.141.175 on eth0 to 255.255.255.255 port 67
DHCPACK of 88.157.141.175 from 10.5.0.1
bound to 88.157.141.175 -- renewal in 728 seconds.
$ ping -c3 www.google.com
ping: unknown host www.google.com
```

No luck :(

---

### Post by chili555 on 2009-06-10
> DHCPOFFER of 88.157.141.175 from 10.5.0.1Well...

88.157.xx.yy looks like an IP address from your internet service provider, *tvtel.pt*. That would be consistent with one computer being connected to a cable modem and getting an IP address directly from *tvtel.pt*. However, 10.5.xx.yy looks like a router, perhaps built in to the cable modem, that gets an 88.157.xx.yy address from *tvtel.pt* and then spreads the connection among several computers who are given 10.5.xx.yy addresses.

Do you have a separate router? Is it hooked up correctly? That is, the cable modem should connect to the router's ***WAN*** port and all the computers should connect to the routers ***LAN*** ports.

---

### Post by Get_It on 2009-06-10
> **chili555 said:**
> Well...

88.157.xx.yy looks like an IP address from your internet service provider, *tvtel.pt*. That would be consistent with one computer being connected to a cable modem and getting an IP address directly from *tvtel.pt*. However, 10.5.xx.yy looks like a router, perhaps built in to the cable modem, that gets an 88.157.xx.yy address from *tvtel.pt* and then spreads the connection among several computers who are given 10.5.xx.yy addresses.

Do you have a separate router? Is it hooked up correctly? That is, the cable modem should connect to the router's ***WAN*** port and all the computers should connect to the routers ***LAN*** ports.
For the time being I'm using a Cisco 800 series router as a hub. Only the output of my previous post was done while I was using this setup. I'm going to connect the laptop directly to my Arris Touchstone modem and run the commands again...

Having done that:
```
 $ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sis190
  State:             connected
  Default:           yes

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         88.157.141.84
    Prefix:          24 (255.255.255.0)
    Gateway:         88.157.141.254

    DNS:             88.157.32.12
    DNS:             88.157.32.77


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             disconnected
  Default:           no

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    goda:            Infra, 00:1C:F0:F5:1C:C4, Freq 2442 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
``````
$ sudo ifconfig wlan0 down
$ sudo /etc/init.d/NetworkManager stop
 * Stopping network connection manager NetworkManager                    [ OK ] 
$ sudo ifconfig eth0 up
$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 3682
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:90:f5:8e:5e:19
Sending on   LPF/eth0/00:90:f5:8e:5e:19
Sending on   Socket/fallback
DHCPREQUEST of 88.157.141.84 on eth0 to 255.255.255.255 port 67
DHCPACK of 88.157.141.84 from 10.5.0.1
bound to 88.157.141.84 -- renewal in 684 seconds.
$ ping -c3 www.google.com
PING www.l.google.com (74.125.39.103) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

```Oh, something different happened... And I still have no idea what the problem is.

Cheers,

---

### Post by chili555 on 2009-06-10
> Oh, something different happened... And I still have no idea what the problem is.Neither do I, but I feel like we're getting closer.> DHCPACK of 88.157.141.84 from 10.5.0.1There is 10.5.0.1 again. If you are connected directly to the modem, this shouldn't be happening. Let's try this:```
sudo dhclient -r
sudo rm /var/lib/dhcp3/dhclient.leases
sudo dhclient eth0
ping -c3 www.google.com
```Does the 10.5.0.1 address disappear? Please also let us see:```
route -n
```Thanks.

---

### Post by Get_It on 2009-06-10
Well, I reconnected the laptop directly to the modem to run those and the mysterious 10.5.0.1 still appears.

```
$ sudo ifconfig wlan0 down
$ sudo /etc/init.d/NetworkManager stop
 * Stopping network connection manager NetworkManager                    [ OK ] 
$ sudo ifconfig eth0 up
$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:90:f5:8e:5e:19  
          inet6 addr: fe80::290:f5ff:fe8a:5b19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12414 (12.4 KB)  TX bytes:5445 (5.4 KB)
          Interrupt:19 Base address:0xdead 
$ sudo dhclient -r
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/d6:b4:57:79:6e:88
Sending on   LPF/pan0/d6:b4:57:79:6e:88
Listening on LPF/wlan0/00:22:43:8a:cd:06
Sending on   LPF/wlan0/00:22:43:8a:cd:06
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:90:f5:8e:5e:19
Sending on   LPF/eth0/00:90:f5:8e:5e:19
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 82.102.32.78 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
$ sudo rm /var/lib/dhcp3/dhclient.leases 
$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:90:f5:8e:5e:19
Sending on   LPF/eth0/00:90:f5:8e:5e:19
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 88.157.141.166 from 10.5.0.1
DHCPREQUEST of 88.157.141.166 on eth0 to 255.255.255.255 port 67
DHCPACK of 88.157.141.166 from 10.5.0.1
bound to 88.157.141.166 -- renewal in 704 seconds.
$ ping -c3 www.google.com
PING www.l.google.com (74.125.39.103) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms
```Now a look at the route -n:
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
88.157.141.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         88.157.141.254  0.0.0.0         UG    0      0        0 eth0
```I also executed the commands again, but this time I didn't shutdown Network Manager:
```
$ sudo dhclient -r
There is already a pid file /var/run/dhclient.pid with pid 3669
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/d6:b4:57:79:6e:88
Sending on   LPF/pan0/d6:b4:57:79:6e:88
Listening on LPF/wlan0/00:22:43:8e:cd:06
Sending on   LPF/wlan0/00:22:43:8e:cd:06
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:90:f5:8e:5e:19
Sending on   LPF/eth0/00:90:f5:8e:5e:19
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 82.102.32.78 port 67
$ sudo rm /var/lib/dhcp3/dhclient.leases 
$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:90:f5:8e:5e:19
Sending on   LPF/eth0/00:90:f5:8e:5e:19
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 88.157.141.166 from 10.5.0.1
DHCPREQUEST of 88.157.141.166 on eth0 to 255.255.255.255 port 67
DHCPACK of 88.157.141.166 from 10.5.0.1
bound to 88.157.141.166 -- renewal in 785 seconds.
$ ping -c3 www.google.com
ping: unknown host www.google.com
``````
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
88.157.141.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         88.157.141.254  0.0.0.0         UG    0      0        0 eth0

```Now my desktop computer, connected through the Cisco router to the same modem spits out the following:
```
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:18:f3:1c:68:c7  
          inet addr:88.157.141.117  Bcast:88.157.141.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:250552 errors:0 dropped:0 overruns:0 frame:1
          TX packets:218578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:62814 txqueuelen:1000 
          RX bytes:219196736 (209.0 MB)  TX bytes:31826175 (30.3 MB)
          Interrupt:19 Base address:0xc400 

$ cat /etc/resolv.conf 
search tvtel.pt
nameserver 88.157.32.12
nameserver 88.157.32.77

$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:18:f3:1c:68:c7
Sending on   LPF/eth0/00:18:f3:1c:68:c7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 88.157.141.244 from 10.5.0.1
DHCPREQUEST of 88.157.141.244 on eth0 to 255.255.255.255 port 67
DHCPACK of 88.157.141.244 from 10.5.0.1
bound to 88.157.141.244 -- renewal in 829 seconds.

$ ping -c3 www.google.com
PING www.l.google.com (74.125.39.106) 56(84) bytes of data.
64 bytes from fx-in-f106.google.com (74.125.39.106): icmp_seq=1 ttl=245 time=59.6 ms
64 bytes from fx-in-f106.google.com (74.125.39.106): icmp_seq=2 ttl=245 time=60.2 ms
64 bytes from fx-in-f106.google.com (74.125.39.106): icmp_seq=3 ttl=245 time=59.6 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 59.625/59.826/60.219/0.277 ms

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
88.157.141.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         88.157.141.254  0.0.0.0         UG    0      0        0 eth0

```Thank you for following up on this chili555.

Cheers,

---

### Post by Get_It on 2009-06-10
Oh, I forgot to mention in my previous post that I'm using Ubuntu 8.10 on my desktop while the laptop has Ubuntu 9.04 installed on it.

Cheers,

---

### Post by Get_It on 2009-06-11
10.5.0.1 is a router at TVTEL to which my cable modem connects.

Cheers,

---

### Post by cariboo on 2009-06-11
There is an isp that does something similar here. On first connect you have to register a mac address with them, could this be your situation?

---

### Post by Get_It on 2009-06-11
> **cariboo907 said:**
> There is an isp that does something similar here. On first connect you have to register a mac address with them, could this be your situation?
I'm lucky to have someone that I know working there and he didn't find anything that could indicate that the problem could be from the ISP side.

The way it works is it only needs to have the cable modem's MAC address registered there, which it is.

Right now I'm using my desktop computer with Ubuntu 8.10 connected by wire to a Cisco router, which is operating as a hub, which in its turn is connected to the cable modem. As you can see I have no problems whatsoever connecting to the Internet on this computer.

You can also see [my desktop's configurations]("http://ubuntuforums.org/showpost.php?p=7436148&postcount=11") in one of my previous posts.

The laptop right now is the only computer here at home having problems using the Internet. Be it to finish the installation/update or to simply ping Google.

Thank you for replying and please continue to give suggestions.

---

### Post by cariboo on 2009-06-11
I had a problem getting my WUA-1340 usb wireless device to connect properly. WHat worked fore me was to uninstall network-manager-gnome and install gnome-network-admin. My wireless device could only see one access point but couldn't connect. To set up the connection go to System-->Administration-->Network select your device.

I can now see and connect to my two access points and see 4 more.

---

### Post by Get_It on 2009-06-11
Thank you everyone for your help and please continue giving ideas to how to solve this.

My main problem right now is with the wired connection.


[LIST]
[*]eth0, ethernet card / wired connection: not working, I mainly need this working since I don't have a wireless network at home and I need to finish installing Ubuntu 9.04 and doing all the updates;
[*]wlan0, wireless connection: not so important right now and I haven't even tried to test this properly yet;
[*]mobile internet connection: I'm more worried about network connections right now.
[/LIST]

I just finished testing the laptop on my brother's network, which has a wireless router/modem. The problem is not from my network and I can access the Internet with the wired connection from the Windows XP on the laptop.

The problem is between the Ubuntu 9.04 and the ethernet cards of the laptop.
I can obtain an IP address (be it an private or public address) but the iptables come up with zero values.

Right now I have to go to bed and get up early in the morning, but as soon as I have time I'll try doing the following: Download the Linux kernel and reinstall it to see if the drivers then work properly. If the previous doesn't work, I'll try reinstalling the *Caixa Mágica 12* distribution that came with the laptop to see if it the wired connection works.

Thank you once again for the help.

Cheers,

---

### Post by Get_It on 2009-06-15
Hi again,
No such luck so far. Everything that I tried didn't work.

The problem is without any doubt between Ubuntu and the ethernet card, it has something to do with the drivers.

If anyone comes up with any suggestions or solutions for this problem please post on this thread.

Thank you very much.

---

### Post by Get_It on 2009-06-17
Update!
I'm trying to see if the ethernet card does work on a Linux distribution. I reinstalled the native distribution which came with the laptop (*Caixa Mágica*) and while it didn't work yesterday; today with did work when I connected **by wire** the laptop to a D-Link wireless router at my brother's house.

I'm going to try some more tests to see if the problem might be with my cable modem. For now I'm going only to test this under the *Caixa Mágica* operative system, since if something is really wrong with the laptop I'll have to send it to the warranty with the original operative system that the computer came with. If nothing goes wrong, I'll later try it on Ubuntu 9.04 and I'll then restart working on the problem from there.

Thanks for the help guys and if you have any new ideas for this please post it.

Cheers,

---

### Post by Get_It on 2009-06-17
Update: I finally got the laptop to get a wired connection at home for the first time while running on *Caixa Mágica*. The problem seemed to be from the cable modem that I was using.

I restarted the computer with a Live CD of Ubuntu 9.04 AMD64. The laptop is able to obtain an IP address through dhclient without any problems, but I'm unable to connect to any website nor a simple ping.

I tried fully installing Ubuntu on the computer, hoping that it would install any drivers that the Live CD might not be using, thus solving the problem, but without any luck.

I'll go over and see your previous suggestions as well try "reinstalling" the kernel and see which kernel *Caixa Mágica* is using.

As always, if you have any suggestions to solve this, please post them here.

Best regards,

---

### Post by Get_It on 2009-06-17
Just figured it out: the problem is in the kernel.

I just tested using the Live CD Ubuntu 9.04 32 bits and the wired connection worked just fine. The problem seems to be in the kernel of Ubuntu 9.04 AMD64.

I'm thinking of sticking to the 32 bit version and later when I don't need the laptop that much I'll try figuring it out how to solve the problem with the AMD64 version.

Have in mind that I'm using kernel 2.6.28-11-generic, could this have already been solved on the recent 2.6.30?

Best regards,

---

