---
title: "Intel 5100 wireless card doesn't connect on 10.04"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by Golden1981 on 2010-06-04
Got a trouble after upgrade to 10.04: cannot connect to Wi-Fi network using the Network Manager.
I have HP ProBook 4310s with Intel WiFi Link 5100 card.
Networks are listed but I can connect to none of them.

Here's some my configuration:
**uname -a:**
```

Linux laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

```

**lspci -nn:**
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series] [1002:9552]
01:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]
03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
86:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:436c] (rev 10)

```

**lshw -c network**
```

  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:aa:8d:58
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:32 memory:d8200000-d8201fff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:86:00.0
       logical name: eth0
       version: 10
       serial: 00:26:55:b4:58:83
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:31 memory:d0100000-d0103fff ioport:2000(size=256) memory:d8e00000-d8e1ffff(prefetchable)

```

**iwconfig:**
```

wlan0     IEEE 802.11abg  ESSID:">\x05\xF1\xEC\xD9g3\xB7\x99P\xA3\xE3\x14\xD3\xD94\xF7^\xA0\xF2\x10\xA8\xF6\x05\x94\x01\xBE\xB4\xBCDx\xFA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

**dmesg | grep iwlagn:**
```

[   20.881491] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   20.881494] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   20.881577] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.881586] iwlagn 0000:03:00.0: setting latency timer to 64
[   20.881618] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100ABG REV=0x54
[   20.921183] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   20.921274] iwlagn 0000:03:00.0: irq 32 for MSI/MSI-X
[   27.200142] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   27.418973] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[ 2018.521168] iwlagn 0000:03:00.0: PCI INT A disabled
[ 2033.241956] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 2033.241959] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 2033.242215] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2033.242249] iwlagn 0000:03:00.0: setting latency timer to 64
[ 2033.242312] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100ABG REV=0x54
[ 2033.282612] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 2033.282698] iwlagn 0000:03:00.0: irq 32 for MSI/MSI-X
[ 2033.294463] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[ 2033.297928] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[ 2114.873584] iwlagn 0000:03:00.0: PCI INT A disabled
[ 2128.053249] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 2128.053252] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 2128.053368] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2128.053401] iwlagn 0000:03:00.0: setting latency timer to 64
[ 2128.053465] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100ABG REV=0x54
[ 2128.093562] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 2128.093646] iwlagn 0000:03:00.0: irq 32 for MSI/MSI-X
[ 2128.104983] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[ 2128.107566] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[ 2253.793394] iwlagn 0000:03:00.0: PCI INT A disabled
[ 2257.992364] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 2257.992367] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 2257.992476] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2257.992509] iwlagn 0000:03:00.0: setting latency timer to 64
[ 2257.992571] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100ABG REV=0x54
[ 2258.032911] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 2258.032995] iwlagn 0000:03:00.0: irq 32 for MSI/MSI-X
[ 2258.042658] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[ 2258.046356] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12

```

**cat /var/log/daemon.log | grep NetworkManager :**
```

Jun  4 11:15:44 golden-laptop NetworkManager: <info>  starting...
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  Trying to start the modem-manager...
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: init!
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:86:00.0/net/eth0, iface: eth0)
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:86:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: end _init.
Jun  4 11:15:44 golden-laptop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  4 11:15:44 golden-laptop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  Found wlan radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: (21575968) ... get_connections.
Jun  4 11:15:44 golden-laptop NetworkManager:    SCPlugin-Ifupdown: (21575968) ... get_connections (managed=false): return empty list.
Jun  4 11:15:44 golden-laptop NetworkManager: Tried to set deprecated property gsm/band
Jun  4 11:15:44 golden-laptop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  (wlan0): now managed
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jun  4 11:15:44 golden-laptop NetworkManager: <info>  (wlan0): bringing up device.
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (wlan0): preparing device.
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jun  4 11:15:45 golden-laptop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (eth0): carrier is OFF
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2')
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (eth0): now managed
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (eth0): bringing up device.
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (eth0): preparing device.
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jun  4 11:15:45 golden-laptop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:86:00.0/net/eth0
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  modem-manager is now available
Jun  4 11:15:45 golden-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  Trying to start the supplicant...
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Jun  4 11:15:45 golden-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jun  4 11:15:46 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/pan0, iface: pan0)
Jun  4 11:15:46 golden-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/pan0, iface: pan0): no ifupdown configuration found.
Jun  4 11:15:46 golden-laptop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/pan0: couldn't determine device driver; ignoring...
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto KCK2'
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto KCK2' has security, but secrets are required.
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto KCK2' has security, and secrets exist.  No new secrets needed.
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCK2'
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun  4 11:18:16 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:18:16 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:18:16 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCK2'.
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:18:19 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:18:20 golden-laptop NetworkManager: <info>  dhclient started with pid 2361
Jun  4 11:18:20 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:18:20 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:18:20 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:18:20 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:18:20 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2361
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (KCK2)
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  Marking connection 'Auto KCK2' invalid.
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:19:05 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto KCK2'
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto KCK2' has security, but secrets are required.
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto KCK2' has security, and secrets exist.  No new secrets needed.
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCK2'
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun  4 11:20:32 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:20:32 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:20:32 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCK2'.
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  dhclient started with pid 2467
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:20:43 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2467
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (KCK2)
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  Marking connection 'Auto KCK2' invalid.
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:21:29 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto KCK2'
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto KCK2' has security, but secrets are required.
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto KCK2' has security, and secrets exist.  No new secrets needed.
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCK2'
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun  4 11:21:49 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:21:49 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:21:49 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCK2'.
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  dhclient started with pid 2471
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:21:52 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2471
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (KCK2)
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  Marking connection 'Auto KCK2' invalid.
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:22:38 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:23:49 golden-laptop NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'kckv'
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'kckv' has security, but secrets are required.
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'kckv' has security, and secrets exist.  No new secrets needed.
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'kckv'
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jun  4 11:23:49 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:23:49 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:23:49 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:24:05 golden-laptop NetworkManager: <info>  wlan0: link timed out.
Jun  4 11:24:50 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jun  4 11:24:50 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:24:50 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jun  4 11:24:50 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:25:05 golden-laptop NetworkManager: <info>  wlan0: link timed out.
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'kckv' has security, and secrets exist.  No new secrets needed.
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'kckv'
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jun  4 11:25:08 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:25:08 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:25:08 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:26:09 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jun  4 11:26:09 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:26:09 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jun  4 11:26:09 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:26:14 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Jun  4 11:26:14 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (kckv)
Jun  4 11:26:14 golden-laptop NetworkManager: <info>  Marking connection 'kckv' invalid.
Jun  4 11:26:14 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:26:14 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:26:14 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:26:24 golden-laptop NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto YURAM'
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto YURAM' requires no security.  No secrets needed.
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'YURAM'
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:26:24 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:26:36 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:26:41 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jun  4 11:26:41 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:27:09 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:27:12 golden-laptop NetworkManager: <info>  wlan0: link timed out.
Jun  4 11:27:14 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jun  4 11:27:14 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:27:25 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation.
Jun  4 11:27:25 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 11)
Jun  4 11:27:25 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (YURAM)
Jun  4 11:27:25 golden-laptop NetworkManager: <info>  Marking connection 'Auto YURAM' invalid.
Jun  4 11:27:25 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:27:25 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:27:25 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:28:12 golden-laptop NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'KCKV'
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'KCKV' has security, but secrets are required.
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:28:12 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'KCKV' has security, and secrets exist.  No new secrets needed.
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCKV'
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jun  4 11:28:13 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:28:13 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:28:13 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCKV'.
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  dhclient started with pid 2589
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:28:16 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:29:02 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:29:02 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2589
Jun  4 11:29:02 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:29:02 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:29:02 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'KCKV'.
Jun  4 11:29:02 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 6 (reason 0)
Jun  4 11:29:02 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jun  4 11:29:02 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'KCKV' has security, and secrets exist.  No new secrets needed.
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCKV'
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jun  4 11:29:07 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:29:07 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:29:07 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:29:17 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCKV'.
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  dhclient started with pid 2625
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:29:21 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:30:06 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:30:06 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2625
Jun  4 11:30:06 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:30:06 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:30:06 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'KCKV'.
Jun  4 11:30:06 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 6 (reason 0)
Jun  4 11:30:06 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jun  4 11:30:06 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'KCKV' has security, and secrets exist.  No new secrets needed.
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCKV'
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jun  4 11:30:27 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:30:27 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCKV'.
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  dhclient started with pid 2644
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:30:27 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:31:13 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:31:13 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2644
Jun  4 11:31:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:31:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:31:13 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'KCKV'.
Jun  4 11:31:13 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 6 (reason 0)
Jun  4 11:31:13 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jun  4 11:31:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'KCKV' has security, and secrets exist.  No new secrets needed.
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCKV'
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jun  4 11:31:56 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:31:56 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:31:56 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:32:06 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:32:11 golden-laptop NetworkManager: <info>  wlan0: link timed out.
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCKV'.
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  dhclient started with pid 2658
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:32:17 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 3 (reason 0)
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2658
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'KCKV'
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'KCKV' has security, but secrets are required.
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (KCKV)
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Marking connection 'KCKV' invalid.
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:33:01 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto KCK2'
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto KCK2' has security, but secrets are required.
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto KCK2' has security, and secrets exist.  No new secrets needed.
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCK2'
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun  4 11:47:23 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:47:23 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:47:23 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:47:26 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:47:26 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCK2'.
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  dhclient started with pid 2826
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:47:27 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2826
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (KCK2)
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  Marking connection 'Auto KCK2' invalid.
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:48:13 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:48:55 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jun  4 11:48:55 golden-laptop NetworkManager: <info>  (wlan0): now unmanaged
Jun  4 11:48:55 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 36)
Jun  4 11:48:55 golden-laptop NetworkManager: <info>  (wlan0): cleaning up...
Jun  4 11:48:55 golden-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  4 11:48:55 golden-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  4 11:48:55 golden-laptop NetworkManager: <info>  Radio killswitch /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill1 disappeared
Jun  4 11:49:10 golden-laptop NetworkManager: <info>  Found wlan radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy1/rfkill2) (driver <unknown>)
Jun  4 11:49:10 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jun  4 11:49:10 golden-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  4 11:49:10 golden-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun  4 11:49:10 golden-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
Jun  4 11:49:10 golden-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jun  4 11:49:10 golden-laptop NetworkManager: <info>  (wlan0): now managed
Jun  4 11:49:10 golden-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jun  4 11:49:10 golden-laptop NetworkManager: <info>  (wlan0): bringing up device.
Jun  4 11:49:10 golden-laptop NetworkManager: <info>  (wlan0): preparing device.
Jun  4 11:49:10 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jun  4 11:49:11 golden-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jun  4 11:49:11 golden-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto KCK2'
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto KCK2' has security, but secrets are required.
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto KCK2' has security, and secrets exist.  No new secrets needed.
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCK2'
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun  4 11:49:21 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:49:21 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:49:21 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCK2'.
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  dhclient started with pid 2894
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:49:24 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2894
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (KCK2)
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  Marking connection 'Auto KCK2' invalid.
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:50:10 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:50:32 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jun  4 11:50:32 golden-laptop NetworkManager: <info>  (wlan0): now unmanaged
Jun  4 11:50:32 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 36)
Jun  4 11:50:32 golden-laptop NetworkManager: <info>  (wlan0): cleaning up...
Jun  4 11:50:32 golden-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  4 11:50:32 golden-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  4 11:50:32 golden-laptop NetworkManager: <info>  Radio killswitch /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy1/rfkill2 disappeared
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  Found wlan radio killswitch rfkill3 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy2/rfkill3) (driver <unknown>)
Jun  4 11:50:45 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jun  4 11:50:45 golden-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/3
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): now managed
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): bringing up device.
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): preparing device.
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jun  4 11:50:45 golden-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jun  4 11:51:09 golden-laptop NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'KCK2'
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'KCK2' has security, but secrets are required.
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'KCK2' has security, and secrets exist.  No new secrets needed.
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCK2'
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun  4 11:51:09 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:51:09 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:51:09 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  4 11:51:14 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCK2'.
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  dhclient started with pid 3070
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:51:17 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3070
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (KCK2)
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  Marking connection 'KCK2' invalid.
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:52:03 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  4 11:52:51 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jun  4 11:52:51 golden-laptop NetworkManager: <info>  (wlan0): now unmanaged
Jun  4 11:52:51 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 36)
Jun  4 11:52:51 golden-laptop NetworkManager: <info>  (wlan0): cleaning up...
Jun  4 11:52:51 golden-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  4 11:52:51 golden-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  4 11:52:51 golden-laptop NetworkManager: <info>  Radio killswitch /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy2/rfkill3 disappeared
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  Found wlan radio killswitch rfkill4 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy3/rfkill4) (driver <unknown>)
Jun  4 11:52:55 golden-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jun  4 11:52:55 golden-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/4
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): now managed
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): bringing up device.
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): preparing device.
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jun  4 11:52:55 golden-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'KCK2'
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'KCK2' has security, but secrets are required.
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'KCK2' has security, and secrets exist.  No new secrets needed.
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Config: added 'ssid' value 'KCK2'
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun  4 11:53:11 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:53:11 golden-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  4 11:53:11 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KCK2'.
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  dhclient started with pid 3104
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  4 11:53:14 golden-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3104
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (KCK2)
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  Marking connection 'KCK2' invalid.
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun  4 11:54:00 golden-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

```

Looking for daemon.log I see that NM cannot obtain DHCP address. But I can't find solution.
This access point KCK2 works perfectly on other ubuntu laptop (9.10) with broadcom card and with my Nokia phone.
Could anybody help me, please?

---

### Post by danielsbrewer on 2011-05-16
Did you find a solution to this?  I am having a very similar problem with the same card.

---

