---
title: "Intrepid + 4965 unable to connect to wpa network"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by Venlaar on 2009-03-02
I have looked through the forums and found many people that have had this problem but haven't yet seen a solution that worked for me. So I am posting this to start a thread specific to my card and problem. I am running a fresh install of intrepid on my Sony Vaio VGN-FZ180E and have not been able to connect to my wpa network. I can connect with no problem to a neighbors unsecured network (used that to run updates). I have tried as many people suggested to install Wicd but after installing the public key apt-get can't seem to find wicd. I also tried under synaptic but it didn't see it either in the Networking (universe). Not that I really think that wicd would make much difference. I did blacklist ipv6 as it prevented connection to even the unsecured network. I will post as much detail below as I can think of to help in case anyone has any ideas about this.

```
dmesg | grep iw
[   13.104560] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.104563] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.314558] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.314572] iwlagn 0000:06:00.0: setting latency timer to 64
[   13.314610] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.364733] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.372812] iwlagn 0000:06:00.0: PCI INT A disabled
[   13.373229] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   25.529095] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   25.529207] iwlagn 0000:06:00.0: restoring config space at offset 0x1 (was 0x40100102, writing 0x40100106)
[   25.529378] firmware: requesting iwlwifi-4965-2.ucode
[   25.798088] Registered led device: iwl-phy0:radio
[   25.798298] Registered led device: iwl-phy0:assoc
[   25.798460] Registered led device: iwl-phy0:RX
[   25.798619] Registered led device: iwl-phy0:TX
```

```
lspci
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

```

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:2a:78:19
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.101 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"NeighborsNet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:08:28:C7   
          Bit Rate=6 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=37/100  Signal level:-78 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

```
tail -f /var/log/syslog
Mar  1 22:01:17 vaio-laptop avahi-daemon[5007]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Mar  1 22:01:18 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Mar  1 22:01:18 vaio-laptop NetworkManager: <info>  Policy set 'Auto linksys' (wlan0) as default for routing and DNS. 
Mar  1 22:01:18 vaio-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Mar  1 22:01:18 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar  1 22:01:18 vaio-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  1 22:01:19 vaio-laptop ntpdate[6018]: adjust time server 91.189.94.4 offset -0.355235 sec
Mar  1 22:09:26 vaio-laptop kernel: [  710.844107] ACPI: EC: missing confirmations, switch off interrupt mode.
Mar  1 22:17:01 vaio-laptop /USR/SBIN/CRON[6119]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  1 22:37:54 vaio-laptop -- MARK --
Mar  1 22:39:45 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Mar  1 22:39:45 vaio-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5938 
Mar  1 22:39:46 vaio-laptop kernel: [ 2530.423752] wlan0: disassociating by local choice (reason=3)
Mar  1 22:39:46 vaio-laptop kernel: [ 2530.425179] wlan0: authenticate with AP 00:16:b6:08:28:c7
Mar  1 22:39:46 vaio-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Mar  1 22:39:46 vaio-laptop avahi-daemon[5007]: Withdrawing address record for 192.168.1.101 on wlan0.
Mar  1 22:39:46 vaio-laptop avahi-daemon[5007]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Mar  1 22:39:46 vaio-laptop avahi-daemon[5007]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar  1 22:39:46 vaio-laptop kernel: [ 2530.427048] wlan0: authenticated
Mar  1 22:39:46 vaio-laptop kernel: [ 2530.427060] wlan0: associate with AP 00:16:b6:08:28:c7
Mar  1 22:39:46 vaio-laptop kernel: [ 2530.429460] wlan0: RX AssocResp from 00:16:b6:08:28:c7 (capab=0x401 status=0 aid=1)
Mar  1 22:39:46 vaio-laptop kernel: [ 2530.429467] wlan0: associated
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto MyNetwork' 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto MyNetwork' has security, but secrets are required. 
Mar  1 22:39:46 vaio-laptop kernel: [ 2530.442944] wlan0: disassociating by local choice (reason=3)
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 0 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto MyNetwork' has security, and secrets exist.  No new secrets needed. 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Config: added 'ssid' value 'MyNetwork' 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Config: added 'group' value 'TKIP WEP40 WEP104 CCMP' 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar  1 22:39:46 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Mar  1 22:39:54 vaio-laptop kernel: [ 2539.145892] wlan0: associate with AP 00:16:b6:08:28:c7
Mar  1 22:39:54 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Mar  1 22:39:54 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Mar  1 22:39:54 vaio-laptop kernel: [ 2539.156198] wlan0: authenticate with AP 00:13:10:ed:62:0a
Mar  1 22:39:54 vaio-laptop kernel: [ 2539.163764] wlan0: authenticate with AP 00:13:10:ed:62:0a
Mar  1 22:39:54 vaio-laptop kernel: [ 2539.163791] wlan0: authenticated
Mar  1 22:39:54 vaio-laptop kernel: [ 2539.163798] wlan0: associate with AP 00:13:10:ed:62:0a
Mar  1 22:39:54 vaio-laptop kernel: [ 2539.168834] wlan0: RX AssocResp from 00:13:10:ed:62:0a (capab=0x431 status=0 aid=1)
Mar  1 22:39:54 vaio-laptop kernel: [ 2539.168848] wlan0: associated
Mar  1 22:39:54 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MyNetwork'. 
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Mar  1 22:39:57 vaio-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar  1 22:39:57 vaio-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar  1 22:39:57 vaio-laptop dhclient: All rights reserved.
Mar  1 22:39:57 vaio-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar  1 22:39:57 vaio-laptop dhclient: 
Mar  1 22:39:57 vaio-laptop dhclient: wmaster0: unknown hardware address type 801
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  dhclient started with pid 6208 
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Mar  1 22:39:57 vaio-laptop dhclient: wmaster0: unknown hardware address type 801
Mar  1 22:39:57 vaio-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Mar  1 22:39:57 vaio-laptop dhclient: Listening on LPF/wlan0/00:13:e8:2a:78:19
Mar  1 22:39:57 vaio-laptop dhclient: Sending on   LPF/wlan0/00:13:e8:2a:78:19
Mar  1 22:39:57 vaio-laptop dhclient: Sending on   Socket/fallback
Mar  1 22:39:59 vaio-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Mar  1 22:40:01 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Mar  1 22:40:01 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Mar  1 22:40:03 vaio-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Mar  1 22:40:12 vaio-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Mar  1 22:40:12 vaio-laptop kernel: [ 2556.329713] wlan0: deauthenticated
Mar  1 22:40:12 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Mar  1 22:40:12 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Mar  1 22:40:13 vaio-laptop kernel: [ 2557.329102] wlan0: authenticate with AP 00:13:10:ed:62:0a
Mar  1 22:40:13 vaio-laptop kernel: [ 2557.330921] wlan0: authenticated
Mar  1 22:40:13 vaio-laptop kernel: [ 2557.330933] wlan0: associate with AP 00:13:10:ed:62:0a
Mar  1 22:40:13 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 5 
Mar  1 22:40:13 vaio-laptop kernel: [ 2557.333585] wlan0: RX ReassocResp from 00:13:10:ed:62:0a (capab=0x431 status=0 aid=1)
Mar  1 22:40:13 vaio-laptop kernel: [ 2557.333597] wlan0: associated
Mar  1 22:40:13 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 4 
Mar  1 22:40:15 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Mar  1 22:40:15 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Mar  1 22:40:15 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Mar  1 22:40:19 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Mar  1 22:40:19 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Mar  1 22:40:22 vaio-laptop kernel: [ 2566.821585] wlan0: deauthenticated
Mar  1 22:40:22 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Mar  1 22:40:22 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Mar  1 22:40:23 vaio-laptop kernel: [ 2567.820129] wlan0: authenticate with AP 00:13:10:ed:62:0a
Mar  1 22:40:23 vaio-laptop kernel: [ 2567.821967] wlan0: authenticated
Mar  1 22:40:23 vaio-laptop kernel: [ 2567.821980] wlan0: associate with AP 00:13:10:ed:62:0a
Mar  1 22:40:23 vaio-laptop kernel: [ 2567.824614] wlan0: RX ReassocResp from 00:13:10:ed:62:0a (capab=0x431 status=0 aid=1)
Mar  1 22:40:23 vaio-laptop kernel: [ 2567.824624] wlan0: associated
Mar  1 22:40:23 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 5 
Mar  1 22:40:23 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 4 
Mar  1 22:40:25 vaio-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Mar  1 22:40:25 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Mar  1 22:40:25 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Mar  1 22:40:25 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Mar  1 22:40:29 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Mar  1 22:40:29 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Mar  1 22:40:32 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Mar  1 22:40:32 vaio-laptop kernel: [ 2576.947954] wlan0: deauthenticated
Mar  1 22:40:32 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Mar  1 22:40:33 vaio-laptop kernel: [ 2577.944106] wlan0: authenticate with AP 00:13:10:ed:62:0a
Mar  1 22:40:33 vaio-laptop kernel: [ 2577.945904] wlan0: authenticated
Mar  1 22:40:33 vaio-laptop kernel: [ 2577.945916] wlan0: associate with AP 00:13:10:ed:62:0a
Mar  1 22:40:33 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 5 
Mar  1 22:40:33 vaio-laptop kernel: [ 2577.948521] wlan0: RX ReassocResp from 00:13:10:ed:62:0a (capab=0x431 status=0 aid=1)
Mar  1 22:40:33 vaio-laptop kernel: [ 2577.948530] wlan0: associated
Mar  1 22:40:33 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 4 
Mar  1 22:40:35 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Mar  1 22:40:36 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Mar  1 22:40:36 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Mar  1 22:40:39 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Mar  1 22:40:39 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Mar  1 22:40:40 vaio-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Mar  1 22:40:42 vaio-laptop kernel: [ 2587.073518] wlan0: deauthenticated
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 6208 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (MyNetwork) 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  Marking connection 'Auto MyNetwork' invalid. 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  Activation (wlan0) failed. 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Mar  1 22:40:42 vaio-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 

```

---

### Post by Venlaar on 2009-03-02
I also followed this post from kevdog on how to connect manually to wpa-psk with no success:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Forgot to mention I am running kernel 2.6.27-11-generic.

Also I am dual booting with Vista and have no problem connecting to the wpa network with Vista.

---

### Post by Venlaar on 2009-03-08
Ok so I installed SuSE 11.1 and had the same problem. I made [a thread in their forum ]("http://forums.opensuse.org/network-internet/wireless/409401-intel-pro-wireless-4965-cant-connect-wpa-network.html") and got some great help but as I found out by trying at a friends wpa network that the problem is actually with my WRK54G v1.1 linksys router. I had downgraded the firmware to 1.58.00 from 1.58.03 quite some time ago because the 1.58.03 firmware was causing the router to lock up about once or twice per day and it would need a reset when this happened. Downgrading the firmware worked as far as keeping it from locking up goes but it looks like it may have caused a problem with different flavors of linux being able to connect to it. So I guess my solution now is going to be to go buy a new router from Best Buy.

---

