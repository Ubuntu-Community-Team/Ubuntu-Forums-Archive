---
title: "Wireless Help Please"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Chaplipman on 2009-06-24
Hello there

I just installed Ubuntu Hardy Heron 8.04 on my Amd64 desktop. Getting online is simple with an Ethernet cable, but I'm having a difficult time getting on with my Wireless usb adapter. Since my whole home network is wireless, I'd like to be able to use the adapter. When I do try to get online with the adapter, I succeed in opening up my homepage, but that's as far as I can usually get. Sometimes I can be online for a couple of minutes, but my connection usually dies immediately. Although my network manager says I'm connected with a strong signal, I'm not. A quick fix to this is reconnecting to my network, but after it refreshes, it does the same crap again and dies. The adapter is a SMC Wireless Ezconnect g USB adapter. Can anyone please help? Here is some additional info from terminal commands.

Ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:2f:35:4c:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:13:f7:94:58:53  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:f7ff:fe94:5853/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:962 errors:41233 dropped:170 overruns:0 frame:41082
          TX packets:2799 errors:44 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:604211 (590.0 KB)  TX bytes:183432465 (174.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:262151 (256.0 KB)  TX bytes:262151 (256.0 KB)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:";]"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:DE:C2:5C   
          Bit Rate=24 Mb/s   
          Link Quality=72/100  Signal level=39/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=1 Destination Host Unreachable
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2010ms
, pipe 3

---

### Post by scrooge_74 on 2009-06-24
[This]("http://www.google.com/linux") is helpfull to the point I found [this]("http://www.linuxquestions.org/hcl/showproduct.php/product/2779") on the first try

Over here is says works out of the box with 8.10 [http://www.debianlinuxhcl.org/browse/product+smc-ez-connect-g---smcwusb-g?id=6679](http://www.debianlinuxhcl.org/browse/product+smc-ez-connect-g---smcwusb-g?id=6679)

---

### Post by RedSingularity on 2009-06-26
How about posting "lspci" from the terminal?

---

