---
title: "wireless card recognised, can ping router but no connection"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by FurryNemesis on 2006-06-26
I;ve been wandering around this forum trying to find a solution for the following problem but so far have had no luck. I have a bt1020 wireless PCMCIA card trying to connect with a linksys router. There is no WEP encryption and  Wireless Assistant and wifi-radar both show me the network, so my card and the network is being picked up. I can ping the router at the normal address (192.168.1.1) but can't get a net connection. I'm thinking it's a DNS error - or I have not installed my card fully. 

Ifconfig shows

eth0      Link encap:Ethernet  HWaddr 00:00:39:9B:AA:DD
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:90:96:43:B0:22
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1177 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0xd100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1844 (1.8 KiB)  TX bytes:1844 (1.8 KiB)

iwconfig shows

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:DA:0E:73
          Bit Rate:11 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

And Interfaces shows


auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid linksys

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth1

 

Any ideas?

*edit* just tried resetting the router and no joy. Also, I can't seem to find my chipset info. Sould I try ndiswrapper anyway?

---

