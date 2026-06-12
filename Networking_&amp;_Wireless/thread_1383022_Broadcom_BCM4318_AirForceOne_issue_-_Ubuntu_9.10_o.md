---
title: "Broadcom BCM4318 AirForceOne issue - Ubuntu 9.10 on Acer Aspire 5024wlmi"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by Zuseppe on 2010-01-16
Hi! I installed Ubuntu 9.10 on my Acer 5024wlmi and followed this [COLOR=Blue]_[guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")_[/COLOR] from Ubuntu community to enable my Broadcom AirForceOne BCM4318 wifi card.
Now the wireless adapter is on (laptop front led also is on), I can see active wifi networks but connection fails (even with a simple ad-hoc open wifi network!). I tried with Network Manager/WICD/Wifi Radar and also using terminal lfconfig/lwconfig commands without success. It seems that my wifi card cannot ping access points: for example see this log from WICD connection session:
```
2010/01/16 22:51:15 :: Connecting to wireless network Winx
2010/01/16 22:51:15 :: /sbin/dhclient -r eth0
2010/01/16 22:51:15 :: ifconfig eth0 0.0.0.0 
2010/01/16 22:51:15 :: /sbin/ip route flush dev eth0
2010/01/16 22:51:15 :: ifconfig eth0 down
2010/01/16 22:51:15 :: ifconfig eth0 up
2010/01/16 22:51:15 :: Putting interface down
2010/01/16 22:51:15 :: ifconfig wlan0 down
2010/01/16 22:51:15 :: iwconfig wlan0
2010/01/16 22:51:15 :: Releasing DHCP leases...
2010/01/16 22:51:15 :: /sbin/dhclient -r wlan0
2010/01/16 22:51:15 :: Setting false IP...
2010/01/16 22:51:15 :: ifconfig wlan0 0.0.0.0 
2010/01/16 22:51:15 :: Stopping wpa_supplicant
2010/01/16 22:51:15 :: wpa_cli -i wlan0 terminate
2010/01/16 22:51:15 :: Flushing the routing table...
2010/01/16 22:51:15 :: /sbin/ip route flush dev wlan0
2010/01/16 22:51:15 :: iwconfig wlan0 mode Ad-Hoc
2010/01/16 22:51:15 :: Putting interface up...
2010/01/16 22:51:15 :: ifconfig wlan0 up
2010/01/16 22:51:15 :: enctype is None
2010/01/16 22:51:15 :: ['iwconfig', 'wlan0', 'essid', 'Winx']
2010/01/16 22:51:15 :: iwconfig wlan0 channel 11
2010/01/16 22:51:15 :: iwconfig wlan0 ap 02:1D:E0:00:08:5A
2010/01/16 22:51:15 :: Setting static IP : 192.168.0.23
2010/01/16 22:51:15 :: ifconfig wlan0 192.168.0.23 netmask 255.255.255.0 
2010/01/16 22:51:15 :: Setting default gateway : 192.168.0.1
2010/01/16 22:51:15 :: route add default gw 192.168.0.1 dev wlan0
2010/01/16 22:51:15 :: Setting DNS : 192.168.0.1
2010/01/16 22:51:15 :: Verifying AP association
2010/01/16 22:51:15 :: ping -q -w 3 -c 1 192.168.0.1
2010/01/16 22:51:17 :: iwconfig wlan0
2010/01/16 22:51:18 :: Connection Failed: Failed to ping the access point!
2010/01/16 22:51:18 :: ifconfig wlan0 0.0.0.0 also
2010/01/16 22:51:18 :: /sbin/ip route flush dev wlan0
2010/01/16 22:51:18 :: wpa_cli -i wlan0 terminate
2010/01/16 22:51:18 :: exiting connection thread
2010/01/16 22:51:19 :: Sending connection attempt result association_failed
```

Here there are some useful data and the output of the commands suggested in "How to post a Wireless issue" guide.

```
Laptop model and Ubuntu version: 
Acer Aspire 5024wlmi laptop
giuseppe@giuseppe-laptop:~$ lsb_release -d
Description:    Ubuntu 9.10
giuseppe@giuseppe-laptop:~$ uname -mr
2.6.31-17-generic i686
``````
giuseppe@giuseppe-laptop:~$ sudo lspci | grep 'Broadcom'
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
``````
giuseppe@giuseppe-laptop:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
giuseppe@giuseppe-laptop:~$ sudo lsmod | grep "b43"
b43                   122168  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  3 acer_wmi,b43,sdhci
ssb                    35364  1 b43

``````
giuseppe@giuseppe-laptop:~$ dmesg | grep b43
[    2.717660] b43-pci-bridge 0000:06:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.884317] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   16.516094] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   16.739725] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   16.745578] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   16.751202] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   16.873265] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   16.912427] Registered led device: b43-phy0::tx
[   16.912449] Registered led device: b43-phy0::rx
[   16.912473] Registered led device: b43-phy0::radio
[   24.644082] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   24.716421] Registered led device: b43-phy0::tx
[   24.716443] Registered led device: b43-phy0::rx
[   24.716464] Registered led device: b43-phy0::radio
[  597.423862] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  597.464433] Registered led device: b43-phy0::tx
[  597.464457] Registered led device: b43-phy0::rx
[  597.464479] Registered led device: b43-phy0::radio
[  646.040035] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  646.096463] Registered led device: b43-phy0::tx
[  646.096486] Registered led device: b43-phy0::rx
[  646.096508] Registered led device: b43-phy0::radio
[  784.870046] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  784.916432] Registered led device: b43-phy0::tx
[  784.916457] Registered led device: b43-phy0::rx
[  784.916479] Registered led device: b43-phy0::radio
[  933.708080] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  933.748489] Registered led device: b43-phy0::tx
[  933.748531] Registered led device: b43-phy0::rx
[  933.748573] Registered led device: b43-phy0::radio
[ 4300.736074] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 4300.776488] Registered led device: b43-phy0::tx
[ 4300.776531] Registered led device: b43-phy0::rx
[ 4300.776575] Registered led device: b43-phy0::radio
``````
giuseppe@giuseppe-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0204000-c0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e8:a2:87
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.242 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1GB/s
       resources: irq:23 ioport:a000(size=256) memory:c0209400-c02094ff memory:44000000-4401ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:49:c7:fc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
``````
giuseppe@giuseppe-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 02:1D:E0:00:08:5A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"Winx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000001035383eb
                    Extra: Last beacon: 272ms ago
                    IE: Unknown: 000457696E78
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010B
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD070050F202000100
``````
giuseppe@giuseppe-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
```Hope you can help me, thanx.

---

### Post by Zuseppe on 2010-01-19
*** UPDATE ****
Hi! I did other experiments and I have an update: the issue is only with
ad-hoc networks.
Moreover yesterday I successufully connected to a Windows ad-hoc
network using Network Manager (that is able to force BSSID address to
grant access to the same cell of the ad-hoc network) following these
steps:

1. I created an ad-hoc network (essid "SkyNet") under WinXPPro, to
share my Internet connection via wireless. To   achieve this result I
manually set 192.168.0.1 IP address and 255.255.255.0 netmask. I also
selected connection sharing option under the adapter connected to the
internet and stopped my firewall.
 2. Connected to the ad-hoc network using my Nokia E52 phone. The
phone and WinXPPro successfully created the network and negotiated IP
addresses via DHCP (note that after connection the phone can access
internet and navigate)
3. At this point, I connected Ubuntu to the ad-hoc network via Network
Manager. dhcpclient founds an active network and connection happens :)
(Note that I later I discovered that I can achieve the same result
skipping step 2 and manually setting a 192.168.0.x address in Ubuntu
via Network Manager profile).

However I still have a problem: even if the connection is established,
I cannot ping the 192.168.0.1 address and the Ubunbtu laptop can't use
the shared internet connection. Here is the syslog printed during the
connection (with dhcp negotiation):

```
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) starting connection 'Auto SkyNet'
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  (wlan0):
device state change: 3 -> 4 (reason 0)
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  (wlan0):
device state change: 4 -> 5 (reason 0)
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0/wireless): connection 'Auto SkyNet' requires no security.  No
secrets needed.
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Config: added
'ssid' value 'SkyNet'
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Config: added
'mode' value '1'
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Config: added
'key_mgmt' value 'NONE'
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Config: set
interface ap_scan to 2
Jan 18 22:30:23 giuseppe-laptop wpa_supplicant[1120]: Trying to
associate with SSID 'SkyNet'
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  (wlan0):
supplicant connection state:  inactive -> scanning
Jan 18 22:30:23 giuseppe-laptop kernel: [ 7513.592066] b43-phy0:
Loading firmware version 410.2160 (2007-05-26 15:32:10)
Jan 18 22:30:23 giuseppe-laptop wpa_supplicant[1120]: Association
request to the driver failed
Jan 18 22:30:23 giuseppe-laptop kernel: [ 7513.632433] Registered led
device: b43-phy0::tx
Jan 18 22:30:23 giuseppe-laptop kernel: [ 7513.632456] Registered led
device: b43-phy0::rx
Jan 18 22:30:23 giuseppe-laptop kernel: [ 7513.632478] Registered led
device: b43-phy0::radio
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  (wlan0):
supplicant connection state:  scanning -> associating
Jan 18 22:30:23 giuseppe-laptop kernel: [ 7513.656215] wlan0: Selected
IBSS BSSID 02:1d:e0:02:63:15 based on configured SSID
Jan 18 22:30:23 giuseppe-laptop wpa_supplicant[1120]: Associated with
02:1d:e0:02:63:15
Jan 18 22:30:23 giuseppe-laptop wpa_supplicant[1120]:
CTRL-EVENT-CONNECTED - Connection to 02:1d:e0:02:63:15 completed
(auth) [id=0 id_str=]
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  (wlan0):
supplicant connection state:  associating -> associated
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  (wlan0):
supplicant connection state:  associated -> completed
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0/wireless) Stage 2 of 5 (Device Configure) successful.
Connected to wireless network 'SkyNet'.
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  (wlan0):
device state change: 5 -> 7 (reason 0)
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 18 22:30:23 giuseppe-laptop dhclient: Internet Systems Consortium
DHCP Client V3.1.2
Jan 18 22:30:23 giuseppe-laptop dhclient: Copyright 2004-2008 Internet
Systems Consortium.
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  dhclient
started with pid 2096
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 18 22:30:23 giuseppe-laptop dhclient: All rights reserved.
Jan 18 22:30:23 giuseppe-laptop dhclient: For info, please visit
http://www.isc.org/sw/dhcp/
Jan 18 22:30:23 giuseppe-laptop dhclient:
Jan 18 22:30:23 giuseppe-laptop NetworkManager: <info>  DHCP: device
wlan0 state changed (null) -> preinit
Jan 18 22:30:23 giuseppe-laptop dhclient: Listening on
LPF/wlan0/00:14:a4:49:c7:fc
Jan 18 22:30:23 giuseppe-laptop dhclient: Sending on
LPF/wlan0/00:14:a4:49:c7:fc
Jan 18 22:30:23 giuseppe-laptop dhclient: Sending on   Socket/fallback
Jan 18 22:30:25 giuseppe-laptop dhclient: DHCPDISCOVER on wlan0 to
255.255.255.255 port 67 interval 8
Jan 18 22:30:25 giuseppe-laptop avahi-daemon[852]: Registering new
address record for fe80::214:a4ff:fe49:c7fc on wlan0.*.
Jan 18 22:30:25 giuseppe-laptop dhclient: DHCPOFFER of 192.168.0.99
from 192.168.0.1
Jan 18 22:30:25 giuseppe-laptop dhclient: DHCPREQUEST of 192.168.0.99
on wlan0 to 255.255.255.255 port 67
Jan 18 22:30:26 giuseppe-laptop dhclient: DHCPACK of 192.168.0.99 from
192.168.0.1
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>  DHCP: device
wlan0 state changed preinit -> bound
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>    address 192.168.0.99
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>    prefix 24
(255.255.255.0)
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>    gateway 192.168.0.1
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>    nameserver
'192.168.0.1'
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>    domain name
'mshome.net'
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 18 22:30:26 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 18 22:30:26 giuseppe-laptop avahi-daemon[852]: Joining mDNS
multicast group on interface wlan0.IPv4 with address 192.168.0.99.
Jan 18 22:30:26 giuseppe-laptop avahi-daemon[852]: New relevant
interface wlan0.IPv4 for mDNS.
Jan 18 22:30:26 giuseppe-laptop avahi-daemon[852]: Registering new
address record for 192.168.0.99 on wlan0.IPv4.
Jan 18 22:30:26 giuseppe-laptop dhclient: bound to 192.168.0.99 --
renewal in 245 seconds.
Jan 18 22:30:27 giuseppe-laptop NetworkManager: <info>  (wlan0):
device state change: 7 -> 8 (reason 0)
Jan 18 22:30:27 giuseppe-laptop NetworkManager: <info>  Policy set
'Auto SkyNet' (wlan0) as default for routing and DNS.
Jan 18 22:30:27 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) successful, device activated.
Jan 18 22:30:27 giuseppe-laptop NetworkManager: <info>  Activation
(wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 18 22:30:34 giuseppe-laptop kernel: [ 7523.992034] wlan0: no IPv6
routers present

```

---

### Post by bkratz on 2010-01-19
All I have found so far are the posting you have made in other languages! except for this one. Although it is specifically referencing Intrepid (so somewhat old)  it may give some clue, it looks like there is some specific information. See post 3 especially

[http://georgia.ubuntuforums.org/showthread.php?t=970624](http://georgia.ubuntuforums.org/showthread.php?t=970624)

---

### Post by Zuseppe on 2010-01-19
bkratz, thanx for the link.
Reading the thread I found another proof that my WIFI adapter is enable and on :)
As you can read [here]("http://www.mjmwired.net/kernel/Documentation/laptops/acer-wmi.txt"):
> 76      Wireless
77	********
78	
79	With regards to wireless, all acer-wmi does is enable the radio on the card. It
80	is not responsible for the wireless LED - once the radio is enabled, this is
81	down to the wireless driver for your card. So the behaviour of the wireless LED,
82	once you enable the radio, will depend on your hardware and driver combination.
83	
84	e.g. With the BCM4318 on the Acer Aspire 5020 series:
85	
86	ndiswrapper: Light blinks on when transmitting
87	b43: Solid light, blinks off when transmitting
88	
89	Wireless radio control is unconditionally enabled - all Acer laptops that support
90	acer-wmi come with built-in wireless.

So you don't have to manually execute acer-wmi under Ubuntu 9.10 on Acer laptops.
My laptop's led shows the same behaviour reported above, except for the blinking :( This means the card doesn't trasmit data, as I suspected in my previous post... 
The problem persists

---

