---
title: "Questions about ath9k and bridging"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by AndrewWalker on 2011-11-29
I've spent weeks trying to get my ath9k wireless card working alongside my r8169 network card in bridged mode but nothing seems to work. I'm trying to build a home router and while I can get the two cards working on separate subnets, nothing seems to get them working in bridged. As far as I can tell, the wireless card does support 'master' mode
 
	Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * WDS
		 * monitor
		 * mesh point
		 * Unknown mode (8)
		 * Unknown mode (9)

and if I set hostapd.conf as this

interface=wlan0
bridge=br0
driver=nl80211

ssid=wirelessnet

channel=6
hw_mode=g

auth_algs=1
wpa=3
wpa_passphrase=password
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP
	 

the wireless network is visible and works but will not work in bridged mode.
Has anyone ever got an ath9k to work in bridged or am I trying to do the impossible?

---

### Post by jonobr on 2011-11-29
Hello

Open to correction but if your trying to connect two dissimilar networks through your machine (ie going from a 192.168.1.x to eg 10.10.1.x)
then you should not be bridging or using br you should be [Routing]("https://help.ubuntu.com/community/Router") between the two interfaces.


Bridging is used for going between two interface on the same network,
I.e your wireless card car would be on the address space 192.168.1.1 to 192.168.1.150 and the lan on 192.168.151 to 192.168.151 to 192.168.1.254

---

### Post by AndrewWalker on 2011-11-30
Sorry, probably didn't do a good job explaining!
I'm trying to bridge eth1 and wlan0 so they are on the same subnet, then my plan is to route eth0 through to br0 and use the box as a firewall/router.

---

### Post by jonobr on 2011-11-30
Hey

Maybe your looking for the equivalent of windows ICS on ubuntu?

[Take a read of this ]("https://help.ubuntu.com/community/Internet/ConnectionSharing")  and see if this is what your looking for

---

### Post by AndrewWalker on 2011-12-02
Thanks, but I'd looked at that page but it didn't quite explain what I needed to know. 
I've got my eth1 and wlan0 bridged now and both are on a 192.168.1.* subnet with working dhcp and I can connect on either wired or wireless networks and access the internet. The only strange thing is I can't ping across the bridged network. I can ping either networks from the server but I can't ping from one host to another with one on wireless and the other on wired even though they are on the same subnet.
Any idea why not? Surely if they are bridged and on the same network this should work?

---

### Post by jonobr on 2011-12-02
Hi 

Could you post your /etc/network/interfaces file so we can see how your bridge is setup?

Thanks

---

### Post by AndrewWalker on 2011-12-02
Here it is,

eth0 is my incoming broadband connection, eth1 and wlan0 are my wired and wireless bridged outgoing connection if that makes sense!


/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet manual
        wireless-mode master
        wireless-essid "frednet2"
        wireless-channel 1

auto br0
iface br0 inet static
        address 192.168.1.1
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        bridge_ports eth1 wlan0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

---

### Post by jonobr on 2011-12-02
I meant to ask for you ifconfig also :-( sorry bout that

---

### Post by AndrewWalker on 2011-12-02
No problem and thanks for your help, here you go


mythuser@MythTVbackend:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 1c:bd:b9:e0:19:ff  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::86c9:b2ff:fe3f:90e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32505 (32.5 KB)  TX bytes:76890 (76.8 KB)

eth0      Link encap:Ethernet  HWaddr f4:6d:04:3c:71:ad  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fe3c:71ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9088212 (9.0 MB)  TX bytes:322389 (322.3 KB)
          Interrupt:45 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 84:c9:b2:3f:90:e7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3384 (3.3 KB)  TX bytes:44264 (44.2 KB)
          Interrupt:20 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:975193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:975193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141285432 (141.2 MB)  TX bytes:141285432 (141.2 MB)

mon.wlan0 Link encap:UNSPEC  HWaddr 1C-BD-B9-E0-19-FF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:480958 (480.9 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:bd:b9:e0:19:ff  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36981 (36.9 KB)  TX bytes:82566 (82.5 KB)

---

### Post by jonobr on 2011-12-02
Hello

I may be misunderstanding your config, but your ETH1 is on a completely different subnet from Eth0?

Bridgind should be between networks on the same subnet,
Again, maybe I am mis reading this info

---

### Post by AndrewWalker on 2011-12-03
Yes, thats because its a dhcp connection to my broadband router, its just been given that ip address by me until it' s ready to be connected. It's eth1 and wlan0 I'm trying to bridge.

---

