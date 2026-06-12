---
title: "wpa_supplicant authentication timed out"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by ls23 on 2010-09-20
Hello everyone,

for weeks now I have the following problem: I am not able to connect to my wireless home network for most of the time. I am using Ubuntu 10.04; an Intel Wifi AGN4965 card and as driver "iwlagn". Maybe the solution lies within these messages (from daemon.log):

Sep 20 22:03:35 ubuntu NetworkManager: <info>  starting...
Sep 20 22:03:35 ubuntu avahi-daemon[1130]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Sep 20 22:03:35 ubuntu avahi-daemon[1130]: Successfully dropped root privileges.
Sep 20 22:03:35 ubuntu avahi-daemon[1130]: avahi-daemon 0.6.25 starting up.
Sep 20 22:03:35 ubuntu avahi-daemon[1130]: Successfully called chroot().
Sep 20 22:03:35 ubuntu avahi-daemon[1130]: Successfully dropped remaining capabilities.
Sep 20 22:03:35 ubuntu avahi-daemon[1130]: No service file found in /etc/avahi/services.
Sep 20 22:03:35 ubuntu avahi-daemon[1130]: Network interface enumeration completed.
Sep 20 22:03:35 ubuntu avahi-daemon[1130]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep 20 22:03:35 ubuntu avahi-daemon[1130]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1600991282.
Sep 20 22:03:35 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Sep 20 22:03:35 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0)
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0/net/wlan0, iface: wlan0)
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Sep 20 22:03:35 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 20 22:03:35 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 20 22:03:35 ubuntu NetworkManager: <info>  Found wlan radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
Sep 20 22:03:35 ubuntu NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/platform/acer-wmi/rfkill/rfkill0) (driver acer-wmi)
Sep 20 22:03:35 ubuntu NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Sep 20 22:03:35 ubuntu NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: (36288800) ... get_connections.
Sep 20 22:03:35 ubuntu NetworkManager:    SCPlugin-Ifupdown: (36288800) ... get_connections (managed=false): return empty list.
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Nokia
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Novatel
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Sierra
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin AnyData
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Option High-Speed
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Gobi
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Ericsson MBM
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Huawei
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Option
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Generic
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin Longcheer
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin MotoC
Sep 20 22:03:35 ubuntu modem-manager: Loaded plugin ZTE
Sep 20 22:03:35 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'ATL1E')
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (eth0): now managed
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (eth0): bringing up device.
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (eth0): preparing device.
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Sep 20 22:03:35 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (wlan0): now managed
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Sep 20 22:03:35 ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Sep 20 22:03:35 ubuntu gdm-binary[1132]: WARNING: Unable to find users: no seat-id found
Sep 20 22:03:35 ubuntu bluetoothd[1233]: Bluetooth daemon 4.60
Sep 20 22:03:35 ubuntu bluetoothd[1236]: Starting SDP server
Sep 20 22:03:35 ubuntu bluetoothd[1236]: Starting experimental netlink support
Sep 20 22:03:35 ubuntu bluetoothd[1236]: Failed to find Bluetooth netlink family
Sep 20 22:03:35 ubuntu bluetoothd[1236]: Failed to init netlink plugin
Sep 20 22:03:35 ubuntu init: apport pre-start process (1245) terminated with status 1
Sep 20 22:03:35 ubuntu acpid: starting up with proc fs
Sep 20 22:03:35 ubuntu init: apport post-stop process (1266) terminated with status 1
Sep 20 22:03:35 ubuntu acpid: 36 rules loaded
Sep 20 22:03:35 ubuntu acpid: waiting for events: event logging is off
Sep 20 22:03:35 ubuntu acpid: client connected from 1288[0:0]
Sep 20 22:03:35 ubuntu acpid: 1 client rule loaded
Sep 20 22:03:36 ubuntu NetworkManager: <info>  (wlan0): preparing device.
Sep 20 22:03:36 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Sep 20 22:03:36 ubuntu NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Sep 20 22:03:36 ubuntu bluetoothd[1236]: bridge pan0 created
Sep 20 22:03:36 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Sep 20 22:03:36 ubuntu NetworkManager: <info>  modem-manager is now available
Sep 20 22:03:36 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Sep 20 22:03:36 ubuntu bluetoothd[1236]: HCI dev 0 registered
Sep 20 22:03:36 ubuntu bluetoothd[1236]: HCI dev 0 up
Sep 20 22:03:36 ubuntu bluetoothd[1236]: Starting security manager 0
Sep 20 22:03:36 ubuntu NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Sep 20 22:03:36 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Sep 20 22:03:36 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/pan0, iface: pan0)
Sep 20 22:03:36 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/pan0, iface: pan0): no ifupdown configuration found.
Sep 20 22:03:36 ubuntu NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/pan0: couldn't determine device driver; ignoring...
Sep 20 22:03:36 ubuntu bluetoothd[1236]: Adapter /org/bluez/1233/hci0 has been enabled
Sep 20 22:03:36 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Sep 20 22:03:37 ubuntu acpid: client connected from 1288[0:0]
Sep 20 22:03:37 ubuntu acpid: 1 client rule loaded
Sep 20 22:03:38 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:03:39 ubuntu rtkit-daemon[1582]: Sucessfully called chroot.
Sep 20 22:03:39 ubuntu rtkit-daemon[1582]: Sucessfully dropped privileges.
Sep 20 22:03:39 ubuntu rtkit-daemon[1582]: Sucessfully limited resources.
Sep 20 22:03:39 ubuntu rtkit-daemon[1582]: Running.
Sep 20 22:03:39 ubuntu rtkit-daemon[1582]: Watchdog thread running.
Sep 20 22:03:39 ubuntu rtkit-daemon[1582]: Canary thread running.
Sep 20 22:03:39 ubuntu polkitd[1586]: started daemon version 0.96 using authority implementation `local' version `0.96'
Sep 20 22:03:39 ubuntu rtkit-daemon[1582]: Sucessfully made thread 1580 of process 1580 (n/a) owned by '114' high priority at nice level -11.
Sep 20 22:03:39 ubuntu rtkit-daemon[1582]: Supervising 1 threads of 1 processes of 1 users.
Sep 20 22:03:40 ubuntu gdm-simple-greeter[1572]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Sep 20 22:03:40 ubuntu acpid: client connected from 1680[108:114]
Sep 20 22:03:40 ubuntu acpid: 1 client rule loaded
Sep 20 22:03:40 ubuntu gdm-session-worker[1574]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep 20 22:03:41 ubuntu rtkit-daemon[1582]: Sucessfully made thread 1682 of process 1580 (n/a) owned by '114' RT at priority 5.
Sep 20 22:03:41 ubuntu rtkit-daemon[1582]: Supervising 2 threads of 1 processes of 1 users.
Sep 20 22:03:41 ubuntu rtkit-daemon[1582]: Sucessfully made thread 1683 of process 1580 (n/a) owned by '114' RT at priority 5.
Sep 20 22:03:41 ubuntu rtkit-daemon[1582]: Supervising 3 threads of 1 processes of 1 users.
Sep 20 22:03:44 ubuntu rtkit-daemon[1582]: Sucessfully made thread 1771 of process 1771 (n/a) owned by '1000' high priority at nice level -11.
Sep 20 22:03:44 ubuntu rtkit-daemon[1582]: Supervising 4 threads of 2 processes of 2 users.
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'neko'
Sep 20 22:03:44 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 20 22:03:44 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'neko' has security, but secrets are required.
Sep 20 22:03:44 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 20 22:03:44 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 20 22:03:44 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'neko' has security, and secrets exist.  No new secrets needed.
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'neko'
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep 20 22:03:44 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 20 22:03:44 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 20 22:03:44 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Sep 20 22:03:44 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Sep 20 22:03:45 ubuntu rtkit-daemon[1582]: Sucessfully made thread 1836 of process 1771 (n/a) owned by '1000' RT at priority 5.
Sep 20 22:03:45 ubuntu rtkit-daemon[1582]: Supervising 5 threads of 2 processes of 2 users.
Sep 20 22:03:45 ubuntu rtkit-daemon[1582]: Sucessfully made thread 1837 of process 1771 (n/a) owned by '1000' RT at priority 5.
Sep 20 22:03:45 ubuntu rtkit-daemon[1582]: Supervising 6 threads of 2 processes of 2 users.
Sep 20 22:03:45 ubuntu rtkit-daemon[1582]: Sucessfully made thread 1839 of process 1839 (n/a) owned by '1000' high priority at nice level -11.
Sep 20 22:03:45 ubuntu rtkit-daemon[1582]: Supervising 7 threads of 3 processes of 2 users.
Sep 20 22:03:46 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:03:46 ubuntu wpa_supplicant[1431]: Trying to associate with 00:19:cb:a1:10:d8 (SSID='neko' freq=2422 MHz)
Sep 20 22:03:46 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 20 22:03:56 ubuntu wpa_supplicant[1431]: Authentication with 00:19:cb:a1:10:d8 timed out.
Sep 20 22:03:56 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Sep 20 22:03:56 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 20 22:03:58 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:03:58 ubuntu wpa_supplicant[1431]: Trying to associate with 00:19:cb:a1:10:d8 (SSID='neko' freq=2422 MHz)
Sep 20 22:03:58 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 20 22:04:08 ubuntu wpa_supplicant[1431]: Authentication with 00:19:cb:a1:10:d8 timed out.
Sep 20 22:04:08 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Sep 20 22:04:08 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 20 22:04:09 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:04:27 ubuntu wpa_supplicant[1431]: last message repeated 2 times
Sep 20 22:04:27 ubuntu NetworkManager: <info>  wlan0: link timed out.
Sep 20 22:04:30 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:04:30 ubuntu wpa_supplicant[1431]: Trying to associate with 00:19:cb:a1:10:d8 (SSID='neko' freq=2432 MHz)
Sep 20 22:04:30 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 20 22:04:40 ubuntu wpa_supplicant[1431]: Authentication with 00:19:cb:a1:10:d8 timed out.
Sep 20 22:04:40 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Sep 20 22:04:40 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 20 22:04:41 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:04:41 ubuntu wpa_supplicant[1431]: Trying to associate with 00:19:cb:a1:10:d8 (SSID='neko' freq=2432 MHz)
Sep 20 22:04:41 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 20 22:04:45 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Sep 20 22:04:45 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Sep 20 22:04:45 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Sep 20 22:04:45 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 20 22:04:46 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 20 22:04:46 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'neko' has security, and secrets exist.  No new secrets needed.
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'neko'
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep 20 22:04:46 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 20 22:04:46 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 20 22:04:46 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Sep 20 22:04:46 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 20 22:04:47 ubuntu AptDaemon: INFO: Initializing daemon
Sep 20 22:04:48 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:04:48 ubuntu wpa_supplicant[1431]: Trying to associate with 00:19:cb:a1:10:d8 (SSID='neko' freq=2432 MHz)
Sep 20 22:04:48 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 20 22:04:58 ubuntu wpa_supplicant[1431]: Authentication with 00:19:cb:a1:10:d8 timed out.
Sep 20 22:04:58 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Sep 20 22:04:58 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 20 22:04:59 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:04:59 ubuntu wpa_supplicant[1431]: Trying to associate with 00:19:cb:a1:10:d8 (SSID='neko' freq=2432 MHz)
Sep 20 22:04:59 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 20 22:05:09 ubuntu wpa_supplicant[1431]: Authentication with 00:19:cb:a1:10:d8 timed out.
Sep 20 22:05:09 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Sep 20 22:05:09 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 20 22:05:11 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:05:11 ubuntu wpa_supplicant[1431]: Trying to associate with 00:19:cb:a1:10:d8 (SSID='neko' freq=2432 MHz)
Sep 20 22:05:11 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 20 22:05:14 ubuntu NetworkManager: <info>  wlan0: link timed out.
Sep 20 22:05:21 ubuntu wpa_supplicant[1431]: Authentication with 00:19:cb:a1:10:d8 timed out.
Sep 20 22:05:21 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Sep 20 22:05:21 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 20 22:05:23 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:05:30 ubuntu wpa_supplicant[1431]: WPS-AP-AVAILABLE 
Sep 20 22:05:30 ubuntu wpa_supplicant[1431]: Trying to associate with 00:19:cb:a1:10:d8 (SSID='neko' freq=2432 MHz)
Sep 20 22:05:30 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 20 22:05:40 ubuntu wpa_supplicant[1431]: Authentication with 00:19:cb:a1:10:d8 timed out.


this goes on... eventually a connection will be established or not. 

I am however able to log into my network if I walk right towards the router - within 1 meter distance the network manager connects right away. After I have established a connection I can disconnect and reconnect as often as I like, network manager will connect to my home network.

Under Windows Vista (dual boot machine) I am able to get a connection everytime...

Your help is greatly appreciated! Thanks in advance!

---

### Post by tirithen on 2010-10-20
I might have the same problem as you, but sadly no solution [http://ubuntuforums.org/showthread.php?t=1589957](http://ubuntuforums.org/showthread.php?t=1589957) I have a different wireless card but the same problem that it works in windows but not in ubuntu. For me the problem is restricted to one access point, it seemes like it is slower than most others at hadeling authentification, on other access points it is no problem.

---

