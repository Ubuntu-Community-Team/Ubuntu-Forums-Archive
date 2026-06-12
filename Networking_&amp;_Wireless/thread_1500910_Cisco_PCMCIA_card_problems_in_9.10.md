---
title: "Cisco PCMCIA card problems in 9.10"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by rgonnering on 2010-06-03
I have a laptop with a Cisco PCMCIA card, that provided flawless wireless operation on 9.04. I have upgraded to 9.10 and it no longer works. I have reviewed lots of complaints about failed wireless on 9.10, and tried lots of remedies, but nothing works. The LEDs on the Cisco PCMCIA are blinking, suggesting that there is network activity.

I (and apparently others) need help.

NO IP Address for eth1 or wifi0:
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:b7:78:a4  
          inet addr:192.168.15.6  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:feb7:78a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:394418 (394.4 KB)  TX bytes:152310 (152.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:0c:30:e9:74:80  
          inet6 addr: fe80::20c:30ff:fee9:7480/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:2691 dropped:0 overruns:0 frame:2691
          TX packets:788 errors:927 dropped:0 overruns:1 carrier:927
          collisions:1 txqueuelen:1000 
          RX bytes:1426 (1.4 KB)  TX bytes:185924 (185.9 KB)
          Interrupt:3 Base address:0x100 

eth1:avahi Link encap:Ethernet  HWaddr 00:0c:30:e9:74:80  
          inet addr:169.254.7.120  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10373 (10.3 KB)  TX bytes:10373 (10.3 KB)

virbr0    Link encap:Ethernet  HWaddr da:d0:a9:55:6e:17  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:20717 (20.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0C-30-E9-74-80-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:6 errors:2691 dropped:0 overruns:0 frame:2691
          TX packets:788 errors:926 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:100 
          RX bytes:1426 (1.4 KB)  TX bytes:185924 (185.9 KB)
          Interrupt:3 Base address:0x100 

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"mot-1-7a"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/100  Signal level=-75 dBm  Noise level=-128 dBm
          Rx invalid nwid:7705  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:40789   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"mot-1-7a"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/100  Signal level=-75 dBm  Noise level=-128 dBm
          Rx invalid nwid:7705  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:40789   Missed beacon:0

virbr0    no wireless extensions.

The essid is correct. The frequency is correct. "Access Point: Invalid" must say something. eth0 is the wired connection and per ifconfig has IP address: 192.168.15.6. Wired works.

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 16892
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0c:30:e9:74:80
Sending on   LPF/eth1/00:0c:30:e9:74:80
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.15.1 port 67
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
Ignoring unknown interface eth0=eth0.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0c:30:e9:74:80
Sending on   LPF/eth1/00:0c:30:e9:74:80
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.

Running $ sudo /etc/init.d/networking restart causes wired to disconnect, but it is readily started with Network Manager. BTW, Network Manager does not have the features it had with 9.04. BTW, Network Manager reports "device not managed" for Wireless Networks.

$ sudo lshw -C network
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:4
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 0c
       serial: 00:03:47:b7:78:a4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.15.6 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:e8120000-e8120fff ioport:1800(size=64) memory:e8100000-e811ffff memory:30100000-3010ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:0c:30:e9:74:80
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS


And if that's not enough, the audio stopped working too with the 9.10 upgrade. In several years of using Ubuntu, this is the first time I feel that I should stop recommending it.

HELP.

---

### Post by Iowan on 2010-06-03
Moved to new thread.

---

