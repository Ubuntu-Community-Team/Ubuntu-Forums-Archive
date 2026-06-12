---
title: "upgrade broke WEP wireless"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by jmccormi on 2008-12-30
Just a couple of days ago I applied some upgrades and now the wireless connection on my laptop will only work if I turn off WEP encryption on my wireless access point (and laptop).  I'm not sure what was in the upgrades, but it had been probably a week or so since I last applied the upgrades.  Prior to the upgrades, WEP encryption worked fine.  The behavior I see is that both the laptop and the wireless access point agree that they have connected, but when the laptop requests an address via DHCP no DHCPOFFERS are received.  Interestingly, I see pretty much the same behavior whether or not I enter the WEP key properly.  (I temporarily chose a very easy to type hex 128 bit key of all 1's to make sure I entered it properly.)

Now the details of my setup:

1 ) Machine Brand and Model (PC/Laptop):

Dell Laptop:  Inspiron 1525

2 ) Wireless Brand, Model and Wireless Chipset:


$ lspci

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


3 ) check interface:

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1d:09:41:1c:0c
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:1f:3c:1a:63:fb
          inet6 addr: fe80::21f:3cff:fe1a:63fb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:17272 (16.8 KB)

eth1:avahi Link encap:Ethernet  HWaddr 00:1f:3c:1a:63:fb
          inet addr:169.254.7.89  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:110600 (108.0 KB)  TX bytes:110600 (108.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-1A-63-FB-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig:

eth1      IEEE 802.11g  ESSID:"z1y2x3w4v5u6"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:01:9A:40:8F
          Bit Rate=54 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality=91/100  Signal level=-39 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


4 ) Check for modules:


Module                  Size  Used by
iwl3945                89844  0
iwlwifi_mac80211      218980  1 iwl3945


5 ) Kernel boot messages


[   24.530991] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   24.530996] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   24.678925] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   26.061579] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels


6 ) Network configuration


  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:41:1c:0c
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:1a:63:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


7 ) Scan for networks:


eth1      No scan results


8 ) Ubuntu Version:


Description:    Ubuntu 8.04.1


9 ) Kernel/architecture (including 32 vs. 64 bit):


2.6.24-22-generic i686


10 ) Restarting the network:


$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...




More details...

I am using nm-applet 0.6.6  (Network Manager)

Here is the (slightly modified - dates and some numbers removed for easy diff'ing) output in /var/log/daemon.log in the (not working) WEP case:

dell-desktop NetworkManager: <info>  starting...
dell-desktop avahi-daemon: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
dell-desktop avahi-daemon: Successfully dropped root privileges.
dell-desktop avahi-daemon: avahi-daemon 0.6.22 starting up.
dell-desktop avahi-daemon: Successfully called chroot().
dell-desktop avahi-daemon: Successfully dropped remaining capabilities.
dell-desktop avahi-daemon: No service file found in /etc/avahi/services.
dell-desktop avahi-daemon: Network interface enumeration completed.
dell-desktop avahi-daemon: Registering HINFO record with values 'I686'/'LINUX'.
dell-desktop avahi-daemon: Server startup complete. Host name is dell-desktop.local. Local service cookie is 3724379260.
dell-desktop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch
dell-desktop NetworkManager: <info>  eth1: Device is fully-supported using driver 'iwl3945'.
dell-desktop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00).
dell-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
dell-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
dell-desktop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'.
dell-desktop NetworkManager: <info>  Deactivating device eth1.
dell-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'.
dell-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
dell-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
dell-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
dell-desktop NetworkManager: <info>  Deactivating device eth0.
dell-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link.
dell-desktop NetworkManager: <debug>  nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_DS_8W1P').
dell-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
dell-desktop hcid: Bluetooth HCI daemon
dell-desktop hcid: Starting SDP server
dell-desktop hcid: Created local server at unix:abstract=/var/run/dbus-gq0pSLSABz,guid=fc236536c7f0ee50746c0b3249599ff9
dell-desktop input: Bluetooth Input daemon
dell-desktop input: Registered input manager path:/org/bluez/input
dell-desktop audio: Bluetooth Audio daemon
dell-desktop audio: Unix socket created: 5
dell-desktop audio: audio.conf: Key file does not have key 'Enable'
dell-desktop audio: audio.conf: Key file does not have key 'Disable'
dell-desktop audio: add_service_record: got record id 0x10000
dell-desktop audio: audio.conf: Key file does not have key 'Disable'
dell-desktop audio: audio.conf: Key file does not have group 'A2DP'
dell-desktop last message repeated 3 times
dell-desktop audio: SEP 0x806d1a0 registered: type:0 codec:0 seid:1
dell-desktop audio: add_service_record: got record id 0x10001
dell-desktop audio: add_service_record: got record id 0x10002
dell-desktop audio: add_service_record: got record id 0x10003
dell-desktop audio: Registered manager path:/org/bluez/audio
dell-desktop NetworkManager: <info>  Will activate connection 'eth0'.
dell-desktop NetworkManager: <info>  Device eth0 activation scheduled...
dell-desktop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported
dell-desktop NetworkManager: <info>  Wireless now enabled by radio killswitch
dell-desktop NetworkManager: <debug>  nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth').
dell-desktop NetworkManager: <info>  Activation (eth0) started...
dell-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
dell-desktop NetworkManager: <info>  Activation (eth0) failure scheduled...
dell-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
dell-desktop NetworkManager: <info>  Activation (eth0) failed.
dell-desktop NetworkManager: <info>  Deactivating device eth0.
dell-desktop NetworkManager: <debug>  nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a02_drm_i915_card0').
dell-desktop hcid: Default passkey agent (:1.19, /org/bluez/passkey) registered
dell-desktop hcid: Default authorization agent (:1.19, /org/bluez/auth) registered
dell-desktop NetworkManager: <info>  Updating allowed wireless network lists.
dell-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'.
dell-desktop NetworkManager: <info>  Will activate connection 'eth1/z1y2x3w4v5u6'.
dell-desktop NetworkManager: <info>  Device eth1 activation scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) started...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
dell-desktop NetworkManager: <info>  Activation (eth1/wireless): access point 'z1y2x3w4v5u6' is encrypted, but NO valid key exists.  New key needed.
dell-desktop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'z1y2x3w4v5u6'.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
dell-desktop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'z1y2x3w4v5u6' received.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
dell-desktop NetworkManager: <info>  Activation (eth1/wireless): access point 'z1y2x3w4v5u6' is encrypted, and a key exists.  No new key needed.
dell-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=1)
dell-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=2)
dell-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=3)
dell-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=4)
dell-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=5)
dell-desktop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
dell-desktop NetworkManager: <info>  SUP: response was '0'
dell-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7a3179327833773476357536'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
dell-desktop NetworkManager: <info>  Supplicant state changed: 1
dell-desktop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'z1y2x3w4v5u6'.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
dell-desktop NetworkManager: <info>  Old device 'eth1' activating, won't change.
dell-desktop avahi-daemon: Registering new address record for fe80::21f:3cff:fe1a:63fb on eth1.*.
dell-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
dell-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1
dell-desktop dhclient: wmaster0: unknown hardware address type 801
dell-desktop dhclient: wmaster0: unknown hardware address type 801
dell-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1
dell-desktop dhclient: DHCPREQUEST of 192.168.0.251 on eth1 to 255.255.255.255 port 67
dell-desktop dhclient: DHCPREQUEST of 192.168.0.251 on eth1 to 255.255.255.255 port 67
dell-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
dell-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
dell-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
dell-desktop dhclient: No DHCPOFFERS received.
dell-desktop dhclient: Trying recorded lease 192.168.0.251
dell-desktop avahi-daemon: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.251.
dell-desktop avahi-daemon: New relevant interface eth1.IPv4 for mDNS.
dell-desktop avahi-daemon: Registering new address record for 192.168.0.251 on eth1.IPv4.
dell-desktop avahi-daemon: Withdrawing address record for 192.168.0.251 on eth1.
dell-desktop avahi-daemon: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.251.
dell-desktop avahi-daemon: Interface eth1.IPv4 no longer relevant for mDNS.
dell-desktop avahi-autoipd(eth1): Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
dell-desktop avahi-autoipd(eth1): Successfully called chroot().
dell-desktop avahi-autoipd(eth1): Successfully dropped root privileges.
dell-desktop avahi-autoipd(eth1): Starting with address 169.254.7.89
dell-desktop avahi-autoipd(eth1): Callout BIND, address 169.254.7.89 on interface eth1
dell-desktop avahi-daemon: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.7.89.
dell-desktop avahi-daemon: New relevant interface eth1.IPv4 for mDNS.
dell-desktop avahi-daemon: Registering new address record for 169.254.7.89 on eth1.IPv4.
dell-desktop avahi-autoipd(eth1): Successfully claimed IP address 169.254.7.89
dell-desktop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started...
dell-desktop NetworkManager: <debug>  real_act_stage4_ip_config_timeout(): Activation (eth1/wireless): could not get IP configuration info for 'z1y2x3w4v5u6', asking for new key.
dell-desktop NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1
dell-desktop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1
dell-desktop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'z1y2x3w4v5u6'.


Here is the same output in the (working) non-WEP case:

dell-desktop NetworkManager: <info>  starting...
dell-desktop avahi-daemon: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
dell-desktop avahi-daemon: Successfully dropped root privileges.
dell-desktop avahi-daemon: avahi-daemon 0.6.22 starting up.
dell-desktop avahi-daemon: Successfully called chroot().
dell-desktop avahi-daemon: Successfully dropped remaining capabilities.
dell-desktop avahi-daemon: No service file found in /etc/avahi/services.
dell-desktop avahi-daemon: Network interface enumeration completed.
dell-desktop avahi-daemon: Registering HINFO record with values 'I686'/'LINUX'.
dell-desktop avahi-daemon: Server startup complete. Host name is dell-desktop.local. Local service cookie is 2662996766.
dell-desktop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch
dell-desktop NetworkManager: <info>  eth1: Device is fully-supported using driver 'iwl3945'.
dell-desktop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00).
dell-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
dell-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
dell-desktop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'.
dell-desktop NetworkManager: <info>  Deactivating device eth1.
dell-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'.
dell-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
dell-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
dell-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
dell-desktop NetworkManager: <info>  Deactivating device eth0.
dell-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link.
dell-desktop NetworkManager: <debug>  nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_DS_8W1P').
dell-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
dell-desktop hcid: Bluetooth HCI daemon
dell-desktop hcid: Starting SDP server
dell-desktop hcid: Created local server at unix:abstract=/var/run/dbus-70CVUSnkAe,guid=e7d004c44b540ff38dbd352f4959a1fe
dell-desktop input: Bluetooth Input daemon
dell-desktop input: Registered input manager path:/org/bluez/input
dell-desktop audio: Bluetooth Audio daemon
dell-desktop audio: Unix socket created: 5
dell-desktop audio: audio.conf: Key file does not have key 'Enable'
dell-desktop audio: audio.conf: Key file does not have key 'Disable'
dell-desktop audio: add_service_record: got record id 0x10000
dell-desktop audio: audio.conf: Key file does not have key 'Disable'
dell-desktop audio: audio.conf: Key file does not have group 'A2DP'
dell-desktop last message repeated 3 times
dell-desktop audio: SEP 0x806d1a0 registered: type:0 codec:0 seid:1
dell-desktop audio: add_service_record: got record id 0x10001
dell-desktop audio: add_service_record: got record id 0x10002
dell-desktop audio: add_service_record: got record id 0x10003
dell-desktop audio: Registered manager path:/org/bluez/audio
dell-desktop NetworkManager: <info>  Will activate connection 'eth0'.
dell-desktop NetworkManager: <info>  Device eth0 activation scheduled...
dell-desktop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported
dell-desktop NetworkManager: <info>  Wireless now enabled by radio killswitch
dell-desktop NetworkManager: <debug>  nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth').
dell-desktop NetworkManager: <info>  Activation (eth0) started...
dell-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
dell-desktop NetworkManager: <info>  Activation (eth0) failure scheduled...
dell-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
dell-desktop NetworkManager: <info>  Activation (eth0) failed.
dell-desktop NetworkManager: <info>  Deactivating device eth0.
dell-desktop NetworkManager: <debug>  nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a02_drm_i915_card0').
dell-desktop hcid: Default passkey agent (:1.19, /org/bluez/passkey) registered
dell-desktop hcid: Default authorization agent (:1.19, /org/bluez/auth) registered
dell-desktop NetworkManager: <info>  Updating allowed wireless network lists.
dell-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'.
dell-desktop NetworkManager: <info>  Will activate connection 'eth1/z1y2x3w4v5u6'.
dell-desktop NetworkManager: <info>  Device eth1 activation scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) started...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
dell-desktop NetworkManager: <info>  Activation (eth1/wireless): access point 'z1y2x3w4v5u6' is unencrypted, no key needed.
dell-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=1)
dell-desktop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
dell-desktop NetworkManager: <info>  SUP: response was '0'
dell-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7a3179327833773476357536'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
dell-desktop NetworkManager: <info>  SUP: response was 'OK'
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
dell-desktop NetworkManager: <info>  Supplicant state changed: 1
dell-desktop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'z1y2x3w4v5u6'.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
dell-desktop NetworkManager: <info>  Old device 'eth1' activating, won't change.
dell-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
dell-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1
dell-desktop dhclient: wmaster0: unknown hardware address type 801
dell-desktop avahi-daemon: Registering new address record for fe80::21f:3cff:fe1a:63fb on eth1.*.
dell-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1
dell-desktop dhclient: wmaster0: unknown hardware address type 801
dell-desktop dhclient: DHCPREQUEST of 192.168.0.251 on eth1 to 255.255.255.255 port 67
dell-desktop dhclient: DHCPACK of 192.168.0.251 from 192.168.0.1
dell-desktop avahi-daemon: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.251.
dell-desktop avahi-daemon: New relevant interface eth1.IPv4 for mDNS.
dell-desktop avahi-daemon: Registering new address record for 192.168.0.251 on eth1.IPv4.
dell-desktop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started...
dell-desktop dhclient: bound to 192.168.0.251 -- renewal in 10005 seconds.
dell-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon:
dell-desktop NetworkManager: <info>    address 192.168.0.251
dell-desktop NetworkManager: <info>    netmask 255.255.255.0
dell-desktop NetworkManager: <info>    broadcast 192.168.0.255
dell-desktop NetworkManager: <info>    gateway 192.168.0.1
dell-desktop NetworkManager: <info>    nameserver 192.168.15.1
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
dell-desktop avahi-daemon: Withdrawing address record for 192.168.0.251 on eth1.
dell-desktop avahi-daemon: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.251.
dell-desktop avahi-daemon: Interface eth1.IPv4 no longer relevant for mDNS.
dell-desktop avahi-daemon: Withdrawing address record for fe80::21f:3cff:fe1a:63fb on eth1.
dell-desktop avahi-daemon: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.251.
dell-desktop avahi-daemon: New relevant interface eth1.IPv4 for mDNS.
dell-desktop avahi-daemon: Registering new address record for 192.168.0.251 on eth1.IPv4.
dell-desktop NetworkManager: <info>  Clearing nscd hosts cache.
dell-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
dell-desktop NetworkManager: <info>  Activation (eth1) Finish handler scheduled.
dell-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
dell-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
dell-desktop avahi-daemon: Registering new address record for fe80::21f:3cff:fe1a:63fb on eth1.*.


I have done me best to search for this problem and solution, but I haven't found what seems to be exactly this same problem.  Any help or pointers would be greatly appreciated.

---

