---
title: "Help with bridge between ubuntu Breezy and Win XP boxes"
date: 2006-05-19
forum: Networking &amp; Wireless
---

### Post by DarkStarDeity on 2006-05-19
After looking at howtos and searching the forums, I managed to set up  a bridge on my ubuntu box (Breezy distro). Both machines can ping each other and the ubuntu machine can access the 'net, but the win machine can't.

In the ubuntu machine I have a netgear wireless card connecting to a ADSL wireless router. I also have an ethernet card connecting to the win box. The ethernet connection is the only network connection the win box has. I installed bridge-utils and configured my /etc/network/interfaces file to create the bridge. This is what the relevant section looks like:

# The primary network interface
auto ath0
iface ath0 inet manual	
#	wireless-mode managed
	wireless-essid <my router name>
	wireless-key restricted <my key>

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
	address 10.1.1.92
	netmask 255.255.255.0
	gateway 10.1.1.1
	bridge_ports eth0 ath0

(NOTE: the line "wireless-mode managed" is commented out because I get the following message when I invoke ifdown if I leave it uncommented - 'Error for wireless request "Set Mode" (8B06) : SET failed on device ath0 ; Invalid argument.' I get this message with or without the bridge being activated, and under various configurations (eg dhcp, static ip). The connection works the same with or without this line, so I just left it out.)

The Win box's config is as follows:
IP Address: 10.1.1.13
Netmask: 255.255.255.0
Deafult Gateway: 10.1.1.92
Preferred DNS Server: 10.1.1.92 
There is currently no firewall on the win box although I do want to put Zone Alarm on it at some stage (I foresee more swearing in my future trying to configure ZA to used a shared connection, but I digress).

The win machine is able to ping 10.1.1.92, so it sees the bridge, but it can't ping 10.1.1.1 (the router), nor any other IP address, so it isn't getting out past the bridge. 

I'm assuming that I need to set up some rules to allow it through the ubuntu firewall, but how do I do that? I tried setting "Enable internet connection sharing" in Firestarter, but it made no difference. I'm having a problem with Firestarter which may be related to my troubles - when I click on "Start Firewall" I get the following error message "Failed to start firewall. The device ath0 is not ready. Please check your network device settings and make sure your internet connection is active." But the device is active and connected to the net - the Network display of Firestarter is even showing packets sent and received. I've tried adding a policy to allow inbound connections from the win box, but I can't apply the policy - I get the same error, that ath0 is not ready. So, how do I fix this problem and how do I get the internet connection shared with the win box through this bridge?

---

### Post by dmizer on 2006-05-19
what do you see when you do ifconfig?  can you post that here?

---

### Post by DarkStarDeity on 2006-05-20
Output of ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:0F:B5:F8:38:77
          inet6 addr: fe80::20f:b5ff:fef8:3877/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:193969 errors:510557 dropped:0 overruns:0 frame:205747
          TX packets:82841 errors:543 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:205286436 (195.7 MiB)  TX bytes:9504113 (9.0 MiB)
          Interrupt:17 Memory:d0ae0000-d0af0000

br0       Link encap:Ethernet  HWaddr 00:0F:B5:F8:38:77
          inet addr:10.1.1.92  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fef8:3877/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:124248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:158029605 (150.7 MiB)  TX bytes:9132068 (8.7 MiB)

eth0      Link encap:Ethernet  HWaddr 00:50:BF:20:62:A8
          inet6 addr: fe80::250:bfff:fe20:62a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:162093 (158.2 KiB)  TX bytes:18285149 (17.4 MiB)
          Interrupt:16 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:778839 errors:0 dropped:0 overruns:0 frame:0
          TX packets:778839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:65976428 (62.9 MiB)  TX bytes:65976428 (62.9 MiB)

Interesting - I just noticed that ath0 and br0 have the same mac address. Is this significant?

---

### Post by DarkStarDeity on 2006-05-20
*bump*

Anybody have an ideas for me?

---

