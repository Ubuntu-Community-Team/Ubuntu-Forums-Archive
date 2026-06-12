---
title: "network manager keeps dropping the wifi signal"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by Yours3lf22 on 2010-12-12
Hi,

I've got a Belkin F5D8055 v1 wifi usb adapter. I use the rt2800usb driver for it. Strangely it uses only 54 Mbit/s instead of 300 Mbit/s. I thought it was ok, since I use the wifi only for accessing the internet. However, the network manager keeps dropping the signal, and I can't understand why. I'm close enough to the router.

iwconfig:

wlan0     IEEE 802.11bgn  ESSID:"MyHomeRouter"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:22:2D:06:2C:50   
          Bit Rate=54 Mb/s   Tx-Power=5 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=51 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:d2:1c:5d  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fed2:1c5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17336444 (17.3 MB)  TX bytes:2379939 (2.3 MB)

I also tried to replace the network manager with wicd but no luck.
Strangely it says that I've got 100% link quality, but in fact I assume I don't.
Another thing is that when I've got a permanent data transfer through wifi (like torrent), it wouldn't drop the signal. Also the when I ping the router sometimes I get 1000ms answering time and the packet loss is also present (around 3%).

Under windows the adapter could do around 80% link quality, 300 Mbit/s, 0% packet loss, and 3ms average ping to the router.

Yours3lf

---

### Post by uncaspi on 2010-12-12
Try to switch the power management of the card off.

sudo iwconfig wlan0 power off rate 300M

---

### Post by Yours3lf22 on 2010-12-13
No luck it seems to have turned off the power management, but I still cant get 300Mbit/s.
I installed a newer compat-wireless driver 2.6.36-4 but the problem still exists, although it now manages to get my link quality, signal level etc. correctly.

Additionally I managed to get an issue when the wifi adapter disconnected, and I copied the content of the system.log file:

[B][U]When I connected:
[/U][/B]> yours3lf-PC kernel: [  302.070018] usb 1-2: new high speed USB device using ehci_hcd and address 5
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/ieee80211/phy2/rfkill2) (driver <unknown>)
Dec 13 16:33:30 yours3lf-PC kernel: [  302.267337] phy2: Selected rate control algorithm 'minstrel'
Dec 13 16:33:30 yours3lf-PC kernel: [  302.267863] Registered led device: rt2800usb-phy2::radio
Dec 13 16:33:30 yours3lf-PC kernel: [  302.267882] Registered led device: rt2800usb-phy2::assoc
Dec 13 16:33:30 yours3lf-PC kernel: [  302.267897] Registered led device: rt2800usb-phy2::quality
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/net/wlan0, iface: wlan0)
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 5)
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/3
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): now managed
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): bringing up device.
Dec 13 16:33:30 yours3lf-PC kernel: [  302.512751] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): preparing device.
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): deactivating device (reason: 2).
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant interface state:  starting -> ready
Dec 13 16:33:30 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Dec 13 16:33:30 yours3lf-PC wpa_supplicant[1075]: Failed to initiate AP scan.
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) starting connection 'Auto MyHomeRouter'
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0/wireless): connection 'Auto MyHomeRouter' has security, and secrets exist.  No new secrets needed.
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Config: added 'ssid' value 'MyHomeRouter'
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Config: added 'scan_ssid' value '1'
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Config: added 'psk' value '<omitted>'
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 13 16:33:31 yours3lf-PC NetworkManager[949]: <info> Config: set interface ap_scan to 1
Dec 13 16:33:40 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Dec 13 16:33:41 yours3lf-PC wpa_supplicant[1075]: Trying to associate with 00:22:2d:06:2c:50 (SSID='MyHomeRouter' freq=2447 MHz)
Dec 13 16:33:41 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec 13 16:33:41 yours3lf-PC kernel: [  314.043330] wlan0: authenticate with 00:22:2d:06:2c:50 (try 1)
Dec 13 16:33:41 yours3lf-PC kernel: [  314.045592] wlan0: authenticated
Dec 13 16:33:41 yours3lf-PC kernel: [  314.046076] wlan0: associate with 00:22:2d:06:2c:50 (try 1)
Dec 13 16:33:41 yours3lf-PC kernel: [  314.048208] wlan0: RX AssocResp from 00:22:2d:06:2c:50 (capab=0x11 status=0 aid=2)
Dec 13 16:33:41 yours3lf-PC kernel: [  314.048211] wlan0: associated
Dec 13 16:33:42 yours3lf-PC wpa_supplicant[1075]: Associated with 00:22:2d:06:2c:50
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  associating -> associated
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec 13 16:33:42 yours3lf-PC kernel: [  314.074923] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 13 16:33:42 yours3lf-PC kernel: [  314.074968] cfg80211: Calling CRDA for country: US
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec 13 16:33:42 yours3lf-PC wpa_supplicant[1075]: WPA: Key negotiation completed with 00:22:2d:06:2c:50 [PTK=CCMP GTK=CCMP]
Dec 13 16:33:42 yours3lf-PC wpa_supplicant[1075]: CTRL-EVENT-CONNECTED - Connection to 00:22:2d:06:2c:50 completed (auth) [id=0 id_str=]
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MyHomeRouter'.
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> dhclient started with pid 1827
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 13 16:33:42 yours3lf-PC dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 13 16:33:42 yours3lf-PC dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 13 16:33:42 yours3lf-PC dhclient: All rights reserved.
Dec 13 16:33:42 yours3lf-PC dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 13 16:33:42 yours3lf-PC dhclient: 
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 13 16:33:42 yours3lf-PC dhclient: Listening on LPF/wlan0/00:1c:df:d2:1c:5d
Dec 13 16:33:42 yours3lf-PC dhclient: Sending on   LPF/wlan0/00:1c:df:d2:1c:5d
Dec 13 16:33:42 yours3lf-PC dhclient: Sending on   Socket/fallback
Dec 13 16:33:42 yours3lf-PC dhclient: DHCPREQUEST of 192.168.2.6 on wlan0 to 255.255.255.255 port 67
Dec 13 16:33:42 yours3lf-PC dhclient: DHCPACK of 192.168.2.6 from 192.168.2.1
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info>   address 192.168.2.6
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info>   prefix 24 (255.255.255.0)
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info>   gateway 192.168.2.1
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info>   nameserver '192.168.2.1'
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info>   domain name 'smcrouter'
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 13 16:33:42 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec 13 16:33:42 yours3lf-PC avahi-daemon[954]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.6.
Dec 13 16:33:42 yours3lf-PC dhclient: bound to 192.168.2.6 -- renewal in 2147483648 seconds.
Dec 13 16:33:42 yours3lf-PC avahi-daemon[954]: New relevant interface wlan0.IPv4 for mDNS.
Dec 13 16:33:42 yours3lf-PC avahi-daemon[954]: Registering new address record for 192.168.2.6 on wlan0.IPv4.
Dec 13 16:33:43 yours3lf-PC avahi-daemon[954]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21c:dfff:fed2:1c5d.
Dec 13 16:33:43 yours3lf-PC avahi-daemon[954]: New relevant interface wlan0.IPv6 for mDNS.
Dec 13 16:33:43 yours3lf-PC avahi-daemon[954]: Registering new address record for fe80::21c:dfff:fed2:1c5d on wlan0.*.
Dec 13 16:33:43 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Dec 13 16:33:43 yours3lf-PC NetworkManager[949]: <info> Policy set 'Auto MyHomeRouter' (wlan0) as default for IPv4 routing and DNS.
Dec 13 16:33:43 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) successful, device activated.
Dec 13 16:33:43 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 13 16:33:49 yours3lf-PC ntpdate[1870]: adjust time server 91.189.94.4 offset 0.083384 sec
Dec 13 16:33:52 yours3lf-PC kernel: [  324.140006] wlan0: no IPv6 routers present 

[U][B]When the driver dropped the connection:
[/B][/U]> 
yours3lf-PC kernel: [  427.980018] No probe response from AP 00:22:2d:06:2c:50 after 500ms, disconnecting.
Dec 13 16:35:35 yours3lf-PC wpa_supplicant[1075]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 13 16:35:35 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Dec 13 16:35:35 yours3lf-PC kernel: [  428.061941] cfg80211: All devices are disconnected, going to restore regulatory settings
Dec 13 16:35:35 yours3lf-PC kernel: [  428.061945] cfg80211: Restoring regulatory settings
Dec 13 16:35:35 yours3lf-PC kernel: [  428.061949] cfg80211: Calling CRDA to update world regulatory domain
Dec 13 16:35:35 yours3lf-PC kernel: [  428.064892] cfg80211: World regulatory domain updated:
Dec 13 16:35:35 yours3lf-PC kernel: [  428.064895]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 13 16:35:35 yours3lf-PC kernel: [  428.064898]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 13 16:35:35 yours3lf-PC kernel: [  428.064901]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 13 16:35:35 yours3lf-PC kernel: [  428.064903]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 13 16:35:35 yours3lf-PC kernel: [  428.064906]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 13 16:35:35 yours3lf-PC kernel: [  428.064908]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 13 16:35:36 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 16:35:37 yours3lf-PC wpa_supplicant[1075]: Trying to associate with 00:22:2d:06:2c:50 (SSID='MyHomeRouter' freq=2447 MHz)
Dec 13 16:35:37 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec 13 16:35:37 yours3lf-PC kernel: [  429.622640] wlan0: authenticate with 00:22:2d:06:2c:50 (try 1)
Dec 13 16:35:37 yours3lf-PC kernel: [  429.820022] wlan0: authenticate with 00:22:2d:06:2c:50 (try 2)
Dec 13 16:35:37 yours3lf-PC kernel: [  430.020030] wlan0: authenticate with 00:22:2d:06:2c:50 (try 3)
Dec 13 16:35:38 yours3lf-PC kernel: [  430.220016] wlan0: authentication with 00:22:2d:06:2c:50 timed out
Dec 13 16:35:43 yours3lf-PC NetworkManager[949]: <info> (wlan0): roamed from BSSID 00:22:2D:06:2C:50 (MyHomeRouter) to (none) ((none))
Dec 13 16:35:47 yours3lf-PC wpa_supplicant[1075]: Authentication with 00:22:2d:06:2c:50 timed out.
Dec 13 16:35:47 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Dec 13 16:35:47 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 16:35:48 yours3lf-PC wpa_supplicant[1075]: Trying to associate with 00:22:2d:06:2c:50 (SSID='MyHomeRouter' freq=2447 MHz)
Dec 13 16:35:48 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec 13 16:35:49 yours3lf-PC kernel: [  441.084165] wlan0: direct probe to 00:22:2d:06:2c:50 (try 1)
Dec 13 16:35:49 yours3lf-PC kernel: [  441.280021] wlan0: direct probe to 00:22:2d:06:2c:50 (try 2)
Dec 13 16:35:49 yours3lf-PC kernel: [  441.480030] wlan0: direct probe to 00:22:2d:06:2c:50 (try 3)
Dec 13 16:35:49 yours3lf-PC kernel: [  441.680014] wlan0: direct probe to 00:22:2d:06:2c:50 timed out
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 8 -> 3 (reason 11)
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): deactivating device (reason: 11).
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1827
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) starting connection 'Auto MyHomeRouter'
Dec 13 16:35:51 yours3lf-PC avahi-daemon[954]: Withdrawing address record for 192.168.2.6 on wlan0.
Dec 13 16:35:51 yours3lf-PC avahi-daemon[954]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.6.
Dec 13 16:35:51 yours3lf-PC avahi-daemon[954]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0/wireless): access point 'Auto MyHomeRouter' has security, but secrets are required.
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0/wireless): connection 'Auto MyHomeRouter' has security, and secrets exist.  No new secrets needed.
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Config: added 'ssid' value 'MyHomeRouter'
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Config: added 'scan_ssid' value '1'
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Config: added 'psk' value '<omitted>'
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> Config: set interface ap_scan to 1
Dec 13 16:35:51 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 16:35:52 yours3lf-PC wpa_supplicant[1075]: Trying to associate with 00:22:2d:06:2c:50 (SSID='MyHomeRouter' freq=2447 MHz)
Dec 13 16:35:52 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec 13 16:35:52 yours3lf-PC kernel: [  444.751199] wlan0: direct probe to 00:22:2d:06:2c:50 (try 1)
Dec 13 16:35:52 yours3lf-PC kernel: [  444.951260] wlan0: direct probe to 00:22:2d:06:2c:50 (try 2)
Dec 13 16:35:53 yours3lf-PC kernel: [  445.150025] wlan0: direct probe to 00:22:2d:06:2c:50 (try 3)
Dec 13 16:35:53 yours3lf-PC kernel: [  445.350027] wlan0: direct probe to 00:22:2d:06:2c:50 timed out
Dec 13 16:36:02 yours3lf-PC wpa_supplicant[1075]: Authentication with 00:22:2d:06:2c:50 timed out.
Dec 13 16:36:02 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Dec 13 16:36:02 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 16:36:04 yours3lf-PC wpa_supplicant[1075]: Trying to associate with 00:22:2d:06:2c:50 (SSID='MyHomeRouter' freq=2447 MHz)
Dec 13 16:36:04 yours3lf-PC NetworkManager[949]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec 13 16:36:04 yours3lf-PC kernel: [  456.221108] wlan0: direct probe to 00:22:2d:06:2c:50 (try 1)
Dec 13 16:36:04 yours3lf-PC kernel: [  456.421265] wlan0: direct probe to 00:22:2d:06:2c:50 (try 2)
Dec 13 16:36:04 yours3lf-PC kernel: [  456.620064] wlan0: direct probe to 00:22:2d:06:2c:50 (try 3)
Dec 13 16:36:04 yours3lf-PC kernel: [  456.820017] wlan0: direct probe to 00:22:2d:06:2c:50 timed out

---

