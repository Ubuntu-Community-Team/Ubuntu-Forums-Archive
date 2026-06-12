---
title: "Wireless Problems Prism 2.5 Intersil"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by ssam1111 on 2009-06-02
Hi,

I am having plenty of problems while getting wireless to work on Ubuntu Jaunty...

I earlier had Ubuntu Hardy and it had complete wireless working. Then I upgraded to Ubuntu Intrepid where Internet completely stopped working. So I connected the box to my laptop with crossover cable so I have internet through my laptop.

I have so far tried following with Intrepid...
I refleshed the hardware with a higher version of firmware..
I have tried orinoco... 
I have blacklisted orinoco, orinoco_pci, hermes..

Then I put the liveCD of Jaunty and in that Wireless was working...
So I upgraded to Jaunty it seemed working... but after sometime it goes off...
I have felt as and when larger data gets transferred it stops functioning. It disconnects itself from the internet..

I was getting ".local hostname..." error I changed the variable AVAHI_DAEMON_DETECT_LOCAL=0 in /etc/default/avahi-daemon file

I upgraded hostapd..

I added following lines to sysctl.conf
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

I tried changing MTU to 1490 for wlan0 but wifi0 was still 1500 I was unable to change that setting.

I am posting the last dmesg messages // I have attached temp.txt which has complete dmesg
[   37.774224] wifi0: LinkStatus=2 (Disconnected)
[   37.795415] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   37.804047] wifi0: LinkStatus=2 (Disconnected)
[   37.817625] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  145.916539] wifi0: LinkStatus=2 (Disconnected)
[  145.928885] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  145.929494] wifi0: LinkStatus=2 (Disconnected)
[  145.929733] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  145.941950] wlan0: Trying to join BSSID 00:1a:1e:91:15:60
[  145.967903] wifi0: LinkStatus=1 (Connected)
[  145.968492] wifi0: LinkStatus: BSSID=00:1a:1e:91:15:60
[  145.969356] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  145.969559] ADDRCONF(NETDEV_CHANGE): wifi0: link becomes ready
[  156.124054] wlan0: no IPv6 routers present
[  541.162514] eth0:  setting half-duplex.
[  753.029950] eth0:  setting half-duplex.
[  789.956538] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  789.956547]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  789.956561]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=33:33:00:00:00:16 A4=00:00:00:00:00:00
[  789.956772] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  789.956778]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  789.956790]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:16 A4=00:00:00:00:00:00
[  790.189353] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  790.189362]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  790.189376]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  790.235143] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  790.235152]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  790.235166]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  790.440308] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  790.440317]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  790.440330]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  790.690857] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  790.690866]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  790.690880]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  790.891358] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  790.891367]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  790.891381]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  790.900482] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  790.900490]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  790.900504]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=33:33:ff:69:ad:57 A4=00:00:00:00:00:00
[  791.422962] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  791.422971]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  791.422985]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  791.900530] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  791.900539]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  791.900554]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=33:33:00:00:00:02 A4=00:00:00:00:00:00
[  792.079830] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  792.079839]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  792.079853]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  792.139810] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  792.139820]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  792.139834]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  792.390163] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  792.390172]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  792.390186]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  792.640689] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  792.640699]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  792.640713]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  792.641231] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  792.641239]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  792.641251]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  792.776457] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  792.776466]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  792.776480]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:16 A4=00:00:00:00:00:00
[  792.841182] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  792.841191]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  792.841205]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  793.611954] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  793.611964]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  793.611978]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  794.030269] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  794.030278]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  794.030291]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  794.268454] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  794.268463]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  794.268477]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  795.900548] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  795.900557]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  795.900570]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=33:33:00:00:00:02 A4=00:00:00:00:00:00
[  796.219565] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  796.219574]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  796.219588]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=01:00:5e:00:00:fb A4=00:00:00:00:00:00
[  798.020470] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  798.020479]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  798.020492]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=33:33:00:00:00:16 A4=00:00:00:00:00:00
[  799.900519] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
[  799.900529]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
[  799.900542]    A1=00:1a:1e:91:15:60 A2=00:60:b3:69:ad:57 A3=33:33:00:00:00:02 A4=00:00:00:00:00:00
[  800.900056] wlan0: no IPv6 routers present
[  801.083275] wifi0: LinkStatus=2 (Disconnected)
[  801.083515] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  801.096212] wifi0: LinkStatus=2 (Disconnected)
[  801.108541] wlan0: Trying to join BSSID 00:1a:1e:91:15:60
[  801.123341] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  801.232460] wifi0: LinkStatus=6 (Association failed)
[  801.232672] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  801.963901] wifi0: LinkStatus=2 (Disconnected)
[  801.965818] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  805.216910] wifi0: LinkStatus=2 (Disconnected)
[  805.237699] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  805.276149] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[  807.177535] ADDRCONF(NETDEV_UP): wifi0: link is not ready
[  807.177598] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  807.761617] wifi0: LinkStatus=2 (Disconnected)
[  807.761856] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  812.156189] wifi0: LinkStatus=2 (Disconnected)
[  812.156420] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  812.169142] wifi0: LinkStatus=2 (Disconnected)
[  812.169373] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  812.181583] wlan0: Trying to join BSSID 00:1a:1e:91:15:60
[  812.383423] wifi0: LinkStatus=6 (Association failed)
[  812.383672] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  827.382292] wifi0: LinkStatus=2 (Disconnected)
[  827.382525] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  827.395215] wifi0: LinkStatus=2 (Disconnected)
[  827.395448] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  827.407671] wlan0: Trying to join BSSID 00:1a:1e:91:15:60
[  827.531581] wifi0: LinkStatus=6 (Association failed)
[  827.531792] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  841.325525] wifi0: LinkStatus=2 (Disconnected)
[  841.325757] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  841.338455] wifi0: LinkStatus=2 (Disconnected)
[  841.338689] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  841.350912] wlan0: Trying to join BSSID 00:1a:1e:91:11:00
[  841.550683] wifi0: LinkStatus=6 (Association failed)
[  841.550895] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  854.955267] wifi0: LinkStatus=2 (Disconnected)
[  854.955500] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  854.968187] wifi0: LinkStatus=2 (Disconnected)
[  854.968422] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  854.980642] wlan0: Trying to join BSSID 00:1a:1e:91:05:00
[  855.104573] wifi0: LinkStatus=6 (Association failed)
[  855.104784] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  867.835161] wifi0: LinkStatus=2 (Disconnected)
[  867.835396] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  947.733420] eth0:  setting half-duplex.

lshw -C network
 *-network:0
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: wifi0
       version: 01
       serial: 00:60:b3:69:ad:57
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.8.2 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:06:de:3a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=3c59x duplex=half ip=192.168.0.85 latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:1f:34:f3:b2:32
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:b0:d0:06:de:3a  
          inet addr:192.168.0.85  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fec0::a:2b0:d0ff:fe06:de3a/64 Scope:Site
          inet6 addr: 2002:80ed:f3e1:a:2b0:d0ff:fe06:de3a/64 Scope:Global
          inet6 addr: fe80::2b0:d0ff:fe06:de3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:468 txqueuelen:1000 
          RX bytes:2602407 (2.6 MB)  TX bytes:622132 (622.1 KB)
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3908 (3.9 KB)  TX bytes:3908 (3.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-60-B3-69-AD-57-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2898055 (2.8 MB)  TX bytes:338223 (338.2 KB)
          Interrupt:11 

wlan0     Link encap:Ethernet  HWaddr 00:60:b3:69:ad:57  
          UP BROADCAST MULTICAST  MTU:1490  Metric:1
          RX packets:2675 errors:0 dropped:5585 overruns:0 frame:0
          TX packets:1995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1698362 (1.6 MB)  TX bytes:338197 (338.1 KB)
          Interrupt:11 

Please let me know if you need any other things...
I have spent around 2-3 days trying to get it to work...

I also thought of loading the driver with ndiswrapper but I could not find a driver package for hostap which has .inf and .sys files...

Thank You
Sam

---

### Post by ssam1111 on 2009-06-03
I have also loaded the net in modules loaded initially so that sysctl.conf comes after the net modules are loaded...

Still haven't got any success...

---

### Post by mightyiam on 2011-10-30
To solve this with this prism2 card I upgraded the firmware on the card to 1.8.2 using this guide:
[http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

---

### Post by nothingspecial on 2011-10-30
Save the necreomancy for Halloween please.

Closed.

---

