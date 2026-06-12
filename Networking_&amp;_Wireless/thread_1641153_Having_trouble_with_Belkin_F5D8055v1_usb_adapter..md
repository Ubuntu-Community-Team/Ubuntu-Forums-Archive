---
title: "Having trouble with Belkin F5D8055v1 usb adapter."
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by badwolfen on 2010-12-08
Hi. I am having trouble with getting my desktop to connect to my wireless router. 

Here are the specs I currently have:
_WIreless Brand:_ Belkin [U]
Wireless Model:[/U] F5D8055 v1
_Wireless Chipset:_ 050d:825a
_Ubuntu Version:_ 10.04.01 LTS
_Machine Brand:_ PC[U]
Kernal Architecture:[/U] 2.6.32-24-generic x86_64

I really am having a problem. I can see wireless networks, but when i try to connect to one, even unsecured, the icon just keeps acting like it is searching for a wifi spot. Im really confused. Please help.

---

### Post by chili555 on 2010-12-09
Please open Applications > Accessories > Terminal and run and then post:```
lsusb
lsmod | grep rt2
```Thanks.

---

### Post by badwolfen on 2010-12-09
Here is the output:
[U]
lsusb:[/U]
> Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 050d:825a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


_lsmod | grep rt2:_
> rt2870sta             525366  0 
rt2800usb              33496  0 
rt2x00usb              11260  1 rt2800usb
rt2x00lib              32133  2 rt2800usb,rt2x00usb
led_class               3764  1 rt2x00lib
mac80211              238448  2 rt2x00usb,rt2x00lib
cfg80211              148546  2 rt2x00lib,mac80211
crc_ccitt               1675  1 rt2800usb


---

### Post by chili555 on 2010-12-09
I believe rt2800usb is correct for your device, not rt2870sta. Please do:```
sudo gedit /etc/modules
```If rt2870sta is in there, please remove it; proofread, save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist rt2870sta
```Proofread, save and close gedit. Now reboot and let us have your report.

---

### Post by badwolfen on 2010-12-09
So I did what you said. I sudo etc/modules and didn't find rt2780sta in there. All it said was:
> 
# /etc/modules: kernal modules to load at boot time
# 
# This file contains the names of kernal modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc


Then I did opened the blacklist and didn't find rt2870sta so I added it to the list. I restarted and the wireless still comes back with no change. :mad:

---

### Post by chili555 on 2010-12-09
Let's see what the kernel has to say:```
dmesg | grep -i rt2
```Thanks.

---

### Post by badwolfen on 2010-12-09
_dmesg | grep -i rt2_
> 
[    8.919054] Registered led device: rt2800usb-phy0::radio
[    8.919068] Registered led device: rt2800usb-phy0::assoc
[    8.919087] Registered led device: rt2800usb-phy0::quality
[    8.919542] usbcore: registered new interface driver rt2800usb
[    8.926515] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    9.564589] rt2800usb 1-4:1.0: firmware: requesting rt2870.bin



---

### Post by chili555 on 2010-12-09
Is a wireless interface created, *wlan0* perhaps?```
iwconfig
```What does this tell us?```
sudo cat /var/log/syslog | grep -e wlan -e etwork
```Thanks.

---

### Post by badwolfen on 2010-12-09
_iwconfig:_
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Badwolfe Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:3F:79:0D:1C   
          Bit Rate=1 Mb/s   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
[U]
sudo cat /var/log/syslog | grep -e wlan -e etwork:[/U]
> Dec  9 22:35:57 ubuntu NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec  9 22:35:57 ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt2800usb')
Dec  9 22:35:57 ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  9 22:35:57 ubuntu NetworkManager: <info>  (wlan0): now managed
Dec  9 22:35:57 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Dec  9 22:35:57 ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (wlan0): preparing device.
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Dec  9 22:35:58 ubuntu NetworkManager: supplicant_interface_acquire:  assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth0): now managed
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth0): bringing up device.
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth0): preparing device.
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Dec  9 22:35:58 ubuntu kernel: [   11.010909] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  9 22:35:58 ubuntu NetworkManager: Added default wired connection  'Auto eth0' for  /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/eth0
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth1): carrier is OFF
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'r8169')
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth1): now managed
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth1): bringing up device.
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth1): preparing device.
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Dec  9 22:35:58 ubuntu NetworkManager: Added default wired connection  'Auto eth1' for  /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/eth1
Dec  9 22:35:58 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/pan0, iface: pan0)
Dec  9 22:35:58 ubuntu NetworkManager:    SCPlugin-Ifupdown: device  added (path: /sys/devices/virtual/net/pan0, iface: pan0): no ifupdown  configuration found.
Dec  9 22:35:58 ubuntu NetworkManager: <WARN>  device_creator():  /sys/devices/virtual/net/pan0: couldn't determine device driver;  ignoring...
Dec  9 22:35:58 ubuntu NetworkManager: <info>  modem-manager is now available
Dec  9 22:35:58 ubuntu NetworkManager: <WARN>   default_adapter_cb(): bluez error getting default adapter: The name  org.bluez was not provided by any .service files
Dec  9 22:35:58 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Dec  9 22:35:58 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Badwolfe Network'
Dec  9 22:36:10 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  9 22:36:10 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation  (wlan0/wireless): access point 'Auto Badwolfe Network' has security, but  secrets are required.
Dec  9 22:36:10 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  9 22:36:10 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  9 22:36:10 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation  (wlan0/wireless): connection 'Auto Badwolfe Network' has security, and  secrets exist.  No new secrets needed.
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'Badwolfe Network'
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Dec  9 22:36:10 ubuntu NetworkManager:  nm_setting_802_1x_get_pkcs11_engine_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
Dec  9 22:36:10 ubuntu NetworkManager:  nm_setting_802_1x_get_pkcs11_module_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  9 22:36:10 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Dec  9 22:36:10 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Dec  9 22:36:12 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:12 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:12 ubuntu kernel: [   24.803915] wlan0: deauthenticating from 00:22:3f:79:0d:1c by local choice (reason=3)
Dec  9 22:36:12 ubuntu kernel: [   24.813902] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:12 ubuntu kernel: [   24.817777] wlan0: direct probe responded
Dec  9 22:36:12 ubuntu kernel: [   24.817780] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:12 ubuntu kernel: [   24.820151] wlan0: authenticated
Dec  9 22:36:12 ubuntu kernel: [   24.820166] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:12 ubuntu kernel: [   24.822777] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:12 ubuntu kernel: [   24.822779] wlan0: associated
Dec  9 22:36:12 ubuntu kernel: [   24.831127] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec  9 22:36:12 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Dec  9 22:36:12 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:13 ubuntu avahi-daemon[918]: Registering new address record for fe80::21c:dfff:fed1:c49e on wlan0.*.
Dec  9 22:36:15 ubuntu kernel: [   27.891402] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:15 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:15 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:16 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:16 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:16 ubuntu kernel: [   29.164021] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:16 ubuntu kernel: [   29.169152] wlan0: direct probe responded
Dec  9 22:36:16 ubuntu kernel: [   29.169154] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:16 ubuntu kernel: [   29.229022] wlan0: authenticated
Dec  9 22:36:16 ubuntu kernel: [   29.229033] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:16 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Dec  9 22:36:16 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec  9 22:36:16 ubuntu kernel: [   29.233024] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:16 ubuntu kernel: [   29.233026] wlan0: associated
Dec  9 22:36:17 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:19 ubuntu kernel: [   32.273905] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:19 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:19 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:20 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:20 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:20 ubuntu kernel: [   33.523903] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:20 ubuntu kernel: [   33.527155] wlan0: direct probe responded
Dec  9 22:36:20 ubuntu kernel: [   33.527158] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:20 ubuntu kernel: [   33.545403] wlan0: authenticated
Dec  9 22:36:20 ubuntu kernel: [   33.545418] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:20 ubuntu kernel: [   33.548529] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:20 ubuntu kernel: [   33.548531] wlan0: associated
Dec  9 22:36:20 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Dec  9 22:36:20 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:22 ubuntu kernel: [   35.531255] wlan0: no IPv6 routers present
Dec  9 22:36:23 ubuntu kernel: [   36.609779] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:24 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:24 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:25 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:25 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:25 ubuntu kernel: [   37.983906] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:25 ubuntu kernel: [   37.987156] wlan0: direct probe responded
Dec  9 22:36:25 ubuntu kernel: [   37.987159] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:25 ubuntu kernel: [   37.997654] wlan0: authenticated
Dec  9 22:36:25 ubuntu kernel: [   37.997668] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:25 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Dec  9 22:36:25 ubuntu kernel: [   38.004409] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:25 ubuntu kernel: [   38.004411] wlan0: associated
Dec  9 22:36:25 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec  9 22:36:26 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:28 ubuntu kernel: [   41.031412] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:28 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:28 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:29 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:29 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:29 ubuntu kernel: [   42.273906] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:29 ubuntu kernel: [   42.278283] wlan0: direct probe responded
Dec  9 22:36:29 ubuntu kernel: [   42.278285] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:29 ubuntu kernel: [   42.280403] wlan0: authenticated
Dec  9 22:36:29 ubuntu kernel: [   42.280416] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:29 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Dec  9 22:36:29 ubuntu kernel: [   42.283030] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:29 ubuntu kernel: [   42.283033] wlan0: associated
Dec  9 22:36:29 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec  9 22:36:30 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:31 ubuntu NetworkManager: <info>  wlan0: link timed out.
Dec  9 22:36:32 ubuntu kernel: [   45.312785] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:32 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:32 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:33 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:33 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:34 ubuntu kernel: [   46.636531] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:34 ubuntu kernel: [   46.640037] wlan0: direct probe responded
Dec  9 22:36:34 ubuntu kernel: [   46.640039] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:34 ubuntu kernel: [   46.657909] wlan0: authenticated
Dec  9 22:36:34 ubuntu kernel: [   46.657923] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:34 ubuntu kernel: [   46.660653] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:34 ubuntu kernel: [   46.660655] wlan0: associated
Dec  9 22:36:34 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Dec  9 22:36:34 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:37 ubuntu kernel: [   49.698282] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:37 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:37 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:38 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:38 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:38 ubuntu kernel: [   50.963907] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:38 ubuntu kernel: [   50.967036] wlan0: direct probe responded
Dec  9 22:36:38 ubuntu kernel: [   50.967038] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:38 ubuntu kernel: [   50.968904] wlan0: authenticated
Dec  9 22:36:38 ubuntu kernel: [   50.968919] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:38 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Dec  9 22:36:38 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec  9 22:36:38 ubuntu kernel: [   50.972154] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:38 ubuntu kernel: [   50.972157] wlan0: associated
Dec  9 22:36:39 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:41 ubuntu kernel: [   53.997785] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:41 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:41 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:42 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:42 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:42 ubuntu kernel: [   55.286530] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:42 ubuntu kernel: [   55.289785] wlan0: direct probe responded
Dec  9 22:36:42 ubuntu kernel: [   55.289788] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:42 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Dec  9 22:36:42 ubuntu kernel: [   55.291405] wlan0: authenticated
Dec  9 22:36:42 ubuntu kernel: [   55.291420] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:42 ubuntu kernel: [   55.294028] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:42 ubuntu kernel: [   55.294030] wlan0: associated
Dec  9 22:36:42 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec  9 22:36:43 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:45 ubuntu kernel: [   58.317659] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:45 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:45 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:46 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:46 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:47 ubuntu kernel: [   59.623405] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:47 ubuntu kernel: [   59.628533] wlan0: direct probe responded
Dec  9 22:36:47 ubuntu kernel: [   59.628536] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:47 ubuntu kernel: [   59.643028] wlan0: authenticated
Dec  9 22:36:47 ubuntu kernel: [   59.643043] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:47 ubuntu kernel: [   59.645654] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:47 ubuntu kernel: [   59.645657] wlan0: associated
Dec  9 22:36:47 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Dec  9 22:36:47 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:48 ubuntu NetworkManager: <info>  wlan0: link timed out.
Dec  9 22:36:50 ubuntu kernel: [   62.710906] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:50 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:50 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:51 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:51 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:51 ubuntu kernel: [   63.963911] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:51 ubuntu kernel: [   63.969911] wlan0: direct probe responded
Dec  9 22:36:51 ubuntu kernel: [   63.969913] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:51 ubuntu kernel: [   63.996908] wlan0: authenticated
Dec  9 22:36:51 ubuntu kernel: [   63.996923] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:51 ubuntu kernel: [   63.999530] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:51 ubuntu kernel: [   63.999533] wlan0: associated
Dec  9 22:36:51 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Dec  9 22:36:51 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:54 ubuntu kernel: [   67.037661] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:54 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:54 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:36:55 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:36:55 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:36:55 ubuntu kernel: [   68.353912] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:55 ubuntu kernel: [   68.357413] wlan0: direct probe responded
Dec  9 22:36:55 ubuntu kernel: [   68.357416] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:55 ubuntu kernel: [   68.359156] wlan0: authenticated
Dec  9 22:36:55 ubuntu kernel: [   68.359172] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:36:55 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Dec  9 22:36:55 ubuntu kernel: [   68.362908] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:36:55 ubuntu kernel: [   68.362911] wlan0: associated
Dec  9 22:36:55 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec  9 22:36:56 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:36:58 ubuntu kernel: [   71.387661] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:36:58 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:36:59 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:37:00 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:37:00 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:37:00 ubuntu kernel: [   72.736794] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:37:00 ubuntu kernel: [   72.740040] wlan0: direct probe responded
Dec  9 22:37:00 ubuntu kernel: [   72.740043] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:37:00 ubuntu kernel: [   72.742909] wlan0: authenticated
Dec  9 22:37:00 ubuntu kernel: [   72.742923] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:37:00 ubuntu kernel: [   72.745916] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:37:00 ubuntu kernel: [   72.745919] wlan0: associated
Dec  9 22:37:00 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Dec  9 22:37:00 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec  9 22:37:01 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:37:03 ubuntu kernel: [   75.780290] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:37:03 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:37:03 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:37:04 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:37:04 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:37:04 ubuntu kernel: [   77.054783] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:37:04 ubuntu kernel: [   77.058035] wlan0: direct probe responded
Dec  9 22:37:04 ubuntu kernel: [   77.058038] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:37:04 ubuntu kernel: [   77.059937] wlan0: authenticated
Dec  9 22:37:04 ubuntu kernel: [   77.059955] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:37:04 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Dec  9 22:37:04 ubuntu kernel: [   77.064674] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:37:04 ubuntu kernel: [   77.064678] wlan0: associated
Dec  9 22:37:04 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec  9 22:37:05 ubuntu NetworkManager: <info>  wlan0: link timed out.
Dec  9 22:37:05 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:37:07 ubuntu kernel: [   80.093285] wlan0: deauthenticated from 00:22:3f:79:0d:1c (Reason: 2)
Dec  9 22:37:07 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:37:07 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 22:37:08 ubuntu wpa_supplicant[1188]: Trying to associate with 00:22:3f:79:0d:1c (SSID='Badwolfe Network' freq=2437 MHz)
Dec  9 22:37:08 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 22:37:08 ubuntu kernel: [   81.363912] wlan0: direct probe to AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:37:08 ubuntu kernel: [   81.367538] wlan0: direct probe responded
Dec  9 22:37:08 ubuntu kernel: [   81.367541] wlan0: authenticate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:37:08 ubuntu kernel: [   81.369657] wlan0: authenticated
Dec  9 22:37:08 ubuntu kernel: [   81.369671] wlan0: associate with AP 00:22:3f:79:0d:1c (try 1)
Dec  9 22:37:08 ubuntu kernel: [   81.372284] wlan0: RX AssocResp from 00:22:3f:79:0d:1c (capab=0x431 status=0 aid=2)
Dec  9 22:37:08 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Dec  9 22:37:08 ubuntu kernel: [   81.372286] wlan0: associated
Dec  9 22:37:08 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 22:37:11 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Dec  9 22:37:11 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Dec  9 22:37:11 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Dec  9 22:37:11 ubuntu kernel: [   83.701290] wlan0: deauthenticating from 00:22:3f:79:0d:1c by local choice (reason=3)
Dec  9 22:37:11 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 22:37:13 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Dec  9 22:37:13 ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (Badwolfe Network)
Dec  9 22:37:13 ubuntu NetworkManager: <info>  Marking connection 'Auto Badwolfe Network' invalid.
Dec  9 22:37:13 ubuntu NetworkManager: <info>  Activation (wlan0) failed.
Dec  9 22:37:13 ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Dec  9 22:37:13 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

---

### Post by chili555 on 2010-12-10
This looks amazingly like you are connected:> wlan0 IEEE 802.11bgn ESSID:"Badwolfe Network"
Mode:Managed Frequency:2.437 GHz [COLOR="Red"]Access Point: 00:22:3F:79:0D:1C[/COLOR]
Bit Rate=1 Mb/s Tx-Power=11 dBm
Retry long limit:7 RTS thrff Fragment thr:off
Power Managementn
[COLOR="Red"]Link Quality=70/70[/COLOR] Signal level=31 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0What does this tell us?```
ifconfig
route -n
```Does any interface have an IP address?

Thanks.

---

### Post by badwolfen on 2010-12-10
_ifconfig:_

> 
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:01:85:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 

eth1      Link encap:Ethernet  HWaddr 00:1f:d0:81:fd:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host


_route -n:_

> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


---

