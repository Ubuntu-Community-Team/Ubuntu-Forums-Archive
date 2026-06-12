---
title: "Belkin G+ MIMO USB Network Adapter &amp; Ubuntu 8.10"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by Drone022 on 2008-12-18
Hey,

I have recently installed Ubuntu 8.10 and I'm trying to configure my wireless access with my Belkin USB adapter. The NetworkManager applet shows the network I'm trying to connect to but is unable to connect. 

I followed this post (RT73 driver - HOW TO):
[http://ubuntuforums.org/showthread.php?t=400236]("http://ubuntuforums.org/showthread.php?t=400236")

I also read this (someone else who had belkin trouble):
[http://ubuntuforums.org/showthread.php?t=691186]("http://ubuntuforums.org/showthread.php?t=691186")

But I still cant get it to connect correctly.

Here's some info.

ifconfig
```
drone@Hook:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:d3:fa:2e:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdd00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

pan0      Link encap:Ethernet  HWaddr ce:04:4d:f2:19:b5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:74:55:a4  
          inet6 addr: fe80::217:3fff:fe74:55a4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:596156 (596.1 KB)  TX bytes:2578 (2.5 KB)
```

Here is iwconfig
```
drone@Hook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-84 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

Then I give it the essid, WEP key and run dhclient
```
drone@Hook:~$ sudo iwconfig wlan0 essid BTHomeHub-5A4F
[sudo] password for drone: 
drone@Hook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"BTHomeHub-5A4F"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-84 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

drone@Hook:~$ sudo iwconfig wlan0 key XXXXXXXXXX
drone@Hook:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:17:3f:74:55:a4
Sending on   LPF/wlan0/00:17:3f:74:55:a4
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
Trying recorded lease 192.168.1.65
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.

--- 192.168.1.254 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```

Here is a bunch more info (edited for relevence):
```
drone@Hook:~$ lsusb
Bus 003 Device 002: ID 03f0:0b0c Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 050d:905b Belkin Components F5D9050 ver 3 Wireless Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

drone@Hook:~$ lsmod | grep usbcore
usbcore               148848  7 rt73,usbhid,usb_storage,libusual,ohci_hcd,ehci_hcd

drone@Hook:~$ dmesg
[   13.430276] rt73: init
[   13.430294] rt73: idVendor = 0x50d, idProduct = 0x905b 

[   15.854377] rt73: using permanent MAC addr
[   15.854381] rt73: Active MAC addr: 00:17:3f:74:55:a4
[   15.854383] rt73: Local MAC = 00:17:3f:74:55:a4
[   15.855707] usbcore: registered new interface driver rt73

[   28.810374] rt73: driver version - 1.0.3.6 CVS
[   28.868368] rt73: using net dev supplied MAC addr
[   28.868381] rt73: Active MAC addr: 00:17:3f:74:55:a4
[   28.868386] rt73: Local MAC = 00:17:3f:74:55:a4
[   29.095533] NET: Registered protocol family 17
[   39.432023] wlan0: no IPv6 routers present

drone@Hook:~$ sudo lshw -C network
[sudo] password for drone: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:fa:2e:61
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:74:55:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:04:4d:f2:19:b5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

drone@Hook:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1D:68:79:E4:79
                    ESSID:"BTHomeHub-5A4F"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Bit Rates:0 kb/s

drone@Hook:~$ lsb_release -d
Description:	Ubuntu 8.10

drone@Hook:~$ uname -mr
2.6.27-9-generic i686

drone@Hook:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...    [ OK ] 

```

It seems the USB adapter is detected and working because it finds the network, there just seems to be a problem actually connecting. Im at a bit of a loss, any help would be greatly appreciated. Thanks!

---

### Post by Drone022 on 2008-12-18
Well, I noticed this line:

[   39.432023] wlan0: no IPv6 routers present

and this line when I ran iwconfig:

inet6 addr: fe80::217:3fff:fe74:55a4/64 Scope:Link

so I disabled ipv6 but it still doesnt seem to have helped.

ip a | grep inet6 doesnt give me anything and the kernel log message has gone so I assume its turned off.

Any help would still be great. I can see the access point but I cant ping it.

---

### Post by Drone022 on 2008-12-19
still no luck, anyone got any ideas?

---

### Post by Drone022 on 2008-12-19
I found out how to fix it.

Reinstall Ubuntu.

---

### Post by reisnoex on 2009-01-24
I'm still having this problem. I used Ubuntu 8.04 with the Belkin USB network adapter with no problems before, but after formatting some disks, I decided to re-install. After the re-installation, it stopped working. I was baffled, because it worked with no problem before. I recently installed 8.10 hoping it would fix the problem, but it hasn't. The adapter shows up as well, along with the network, but I can't connect. This is a fresh install too, so I don't see how a re-install would fix it. I'm new to linux and these forums, so I'm not sure what technical information I could give that would help. I want to get to the center of this problem though. :)

---

### Post by zenial on 2009-01-24
i guess u fixed ur own prob heheh

---

### Post by reisnoex on 2009-01-24
No. Drone022's problem was fixed with a re-install. I'm sitting here with a fresh install, and it's not working. It recognizes the adapter, and the network, but I can't connect to it. I'm going to try using NDISwrapper and see how that goes.

---

### Post by reisnoex on 2009-01-25
The solution was as simple as unplugging the wireless dongle and plugging it back in. It was a conflict between booting Ubuntu directly after shutting down Windows. Good times.

---

