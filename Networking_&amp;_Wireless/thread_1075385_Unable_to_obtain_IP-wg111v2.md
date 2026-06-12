---
title: "Unable to obtain IP-wg111v2"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by Corniger on 2009-02-20
Hi guys!

I'm really about to give up on this, so I tried to gather as much info as possibel so maybe somebody can help me out.

I already uninstalled Network Manager and git WICD instead, but it also fails to connect to the WLan. After "obtaining IP" everything is the same like with Network Manager - "Disconnected"

I've tried all sorts of guides already, but either I need an internet connection to get an internet connection, or the guide is outdated and refers to menu items that don't exist in intrepid anymore. So please, don't refer me to any of those ;)

I've also tried Keryx, but still I can't get a connection or install the needed 3d Graphics driver from NVidia - except if I have a connection. My system is up to date thanks to Keryx, but still there are core basics missing.

I also tried to edit the "interfaces" file and add the two magic lines people were talking about in another thread (with wlan0 instead of eth0) but I wasn't allowed to save the file.

I know I could hard code a static IP, but how? I HAVE a static ip that I could easily obtain from the windows system on that machine, but I've read that it is no use because of DHCP or so.

Here's all the info I know that could be important.

> 
sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"gHeimnetz"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:99:30:D4   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:EE59-03F9-DF1A-017A-E9E5-3D19-8695-0A2B-212F-226D-848B-6252-BD35-046A-0380-41EA [2]   Security mode:open
          Power Management:off
          Link Quality=46/100  Signal level:49/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


> 
sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:e0:10:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:c0:85:b0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:238961 (238.9 KB)  TX bytes:14931 (14.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-B5-C0-85-B0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

> 
sudo ping -c 4 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.054 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.055 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.051 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.054 ms

--- localhost ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.051/0.053/0.055/0.007 ms

> 
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on
> 
 sudo lshw -C network
[sudo] password for hula: 
  *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:c0:85:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:c9:13:11:52:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

> 
sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0f:b5:c0:85:b0
Sending on   LPF/wlan0/00:0f:b5:c0:85:b0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

> 
switched off ipv6



Edit: added stuff
put in static IP. No success.


OK, that's it. PLEASE! HELP!

---

