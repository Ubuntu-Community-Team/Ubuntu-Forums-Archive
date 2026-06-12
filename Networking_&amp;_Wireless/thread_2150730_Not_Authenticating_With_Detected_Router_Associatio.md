---
title: "Not Authenticating With Detected Router: Association request to the driver failed"
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by drblitzen on 2013-06-02
On my Dell Studio laptop in Windows 7, I'm able to connect to a certain wifi router (named "zrtspshome@unifi"), and it says it's connecting with WPA2 using AES encryption.

Rebooting into Ubuntu 12.04, I see all the wifi routers in the area, and could previously connect to other ones of the same company and brand, but when trying to connect to this one with the same password that works in Windows, it fails authentication and dumps the following to /var/log/syslog:

```

Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): disconnecting for new activation request.
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): device state change: need-auth -> disconnected (reason 'none') [60 30 0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): deactivating device (reason 'none') [0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) starting connection 'zrtspshome@unifi 1'
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1/wireless): access point 'zrtspshome@unifi 1' has security, but secrets are required.
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  2 10:42:15 bobstudio NetworkManager[919]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1/wireless): connection 'zrtspshome@unifi 1' has security, and secrets exist.  No new secrets needed.
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'ssid' value 'zrtspshome@unifi'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'scan_ssid' value '1'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'auth_alg' value 'OPEN'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'psk' value '<omitted>'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: set interface ap_scan to 1
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jun  2 10:42:15 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:15 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:20 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:21 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:22 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:22 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:22 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:27 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:27 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:28 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:28 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:28 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:33 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:33 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:35 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:35 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:35 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:40 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:40 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:40 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:40 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:40 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:45 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:45 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:47 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:47 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:47 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:52 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:52 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:53 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:53 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:53 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:58 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:58 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:43:00 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:43:00 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:43:00 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:43:05 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:43:05 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:43:05 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:43:05 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:43:05 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:43:10 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:43:10 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:43:12 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:43:12 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:43:12 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:43:15 bobstudio NetworkManager[919]: <warn> Activation (eth1/wireless): association took too long.
Jun  2 10:43:15 bobstudio NetworkManager[919]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  2 10:43:15 bobstudio NetworkManager[919]: <warn> Activation (eth1/wireless): asking for new secrets
Jun  2 10:43:15 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> disconnected
Jun  2 10:43:15 bobstudio NetworkManager[919]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): disconnecting for new activation request.
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): device state change: need-auth -> disconnected (reason 'none') [60 30 0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): deactivating device (reason 'none') [0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) starting connection 'zrtspshome@unifi 1'
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1/wireless): access point 'zrtspshome@unifi 1' has security, but secrets are required.
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  2 10:42:00 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  2 10:42:15 bobstudio NetworkManager[919]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1/wireless): connection 'zrtspshome@unifi 1' has security, and secrets exist.  No new secrets needed.
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'ssid' value 'zrtspshome@unifi'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'scan_ssid' value '1'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'auth_alg' value 'OPEN'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: added 'psk' value '<omitted>'
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> Config: set interface ap_scan to 1
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jun  2 10:42:15 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:15 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:15 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:20 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:21 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:22 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:22 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:22 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:27 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:27 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:28 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:28 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:28 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:33 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:33 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:35 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:35 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:35 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:40 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:40 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:40 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:40 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:40 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:45 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:45 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:47 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:47 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:47 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:52 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:52 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:42:53 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:42:53 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:42:53 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:42:58 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:42:58 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:43:00 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:43:00 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:43:00 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:43:05 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:43:05 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:43:05 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:43:05 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:43:05 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:43:10 bobstudio wpa_supplicant[1219]: Authentication with cc:b2:55:d0:e4:36 timed out.
Jun  2 10:43:10 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> scanning
Jun  2 10:43:12 bobstudio wpa_supplicant[1219]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  2 10:43:12 bobstudio wpa_supplicant[1219]: Association request to the driver failed
Jun  2 10:43:12 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 10:43:15 bobstudio NetworkManager[919]: <warn> Activation (eth1/wireless): association took too long.
Jun  2 10:43:15 bobstudio NetworkManager[919]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  2 10:43:15 bobstudio NetworkManager[919]: <warn> Activation (eth1/wireless): asking for new secrets
Jun  2 10:43:15 bobstudio NetworkManager[919]: <info> (eth1): supplicant interface state: associating -> disconnected
Jun  2 10:43:15 bobstudio NetworkManager[919]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

```

Here are some more diagnostic details:

lshw -C network
```

*-network
Description: Kabellose Verbindung
Product: BCM4313 802.11b/g/n Wireless LAN Controller
Vendor: Broadcom Corporation
Physical ID: 0
Bus-Info: pci@0000:04:00.0
Logical Name: eth1
Version: 01
Serial: 70:f1:a1:fc:3d:c3
Width: 64 bits
Clock: 33MHz
Capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
konfiguration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
Resources: irq:17 memory:f0500000-f0503fff
(also lists NIC)

```

lspci -nn|grep 0280
```

04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

iwconfig
```

lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11abg ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=200 dBm
Retry long limit:7 RTS thrff Fragment thrff
Encryption keyff
Power Managementff

```

rfkill list all
```

0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
1: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no
2: dell-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no

```

dmesg|grep eth1
```

[ 21.122635] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)

```

ifconfig eth1
```

eth1 Link encap:Ethernet Hardware Adresse 70:f1:a1:fc:3d:c3
inet6-Adresse: fe80::72f1:a1ff:fefc:3dc3/64 GÃ¼ltigkeitsbereich:Verbindung
UP BROADCAST MULTICAST MTU:1500 Metrik:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:22
TX packets:0 errors:20 dropped:0 overruns:0 carrier:0
Kollisionen:0 SendewarteschlangenlÃ¤nge:1000
RX-Bytes:0 (0.0 B) TX-Bytes:0 (0.0 B)
Interrupt:17


```

iwconfig eth1
```

eth1 IEEE 802.11abg ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=200 dBm
Retry long limit:7 RTS thrff Fragment thrff
Encryption keyff
Power Managementff


```

iwlist scan
```

lo Interface doesn't support scanning.

eth1 Scan completed :
Cell 01 - Address: CC:B2:550:E4:36
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=37/70 Signal level=-73 dBm
Encryption keyn
ESSID:"zrtspshome@unifi"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 92ms ago
IE: Unknown: 00107A7274737073686F6D6540756E696669
IE: Unknown: 010882848B960C121824
IE: Unknown: 030102
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1602050000000000000000000000000000000000000000
IE: Unknown: 4A0E14000A00B400C800140005001900
IE: Unknown: 7F0101
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3402050000000000000000000000000000000000000000
IE: Unknown: DD0600E04C020160

[...and 14 more...]

```

lsb_release -d
```

Description: Ubuntu 12.04.2 LTS

```

uname -mr
```

3.2.0-34-generic x86_64

```

(lsmod doesn't show anything wireless-related; I'm using the built-in kernel driver that came with Ubuntu 12.04.)

Interestingly, looking at the list of saved wifi connections, after several attempts a 2nd entry of the same name but with a "1" tacked onto the end eventually appears, followed later by another with a "2", etc., as if it's finding it as a new connection. Also, after these attempts I'm suddenly unable to authenticate with the previous router as well.

It has usually been the case that the Linux boot needs more fiddling before seeing and connecting to the same networks that Windows can. Bad driver perhaps?

---

### Post by Hadaka on 2013-06-02
Hi, your iwlist shows..

Pairwise Ciphers (2) : TKIP CCMP

try removing the TKIP in your router settings
and it should then connect..

thanks.

---

### Post by drblitzen on 2013-06-02
> **Hadaka said:**
> Hi, your iwlist shows..

Pairwise Ciphers (2) : TKIP CCMP

try removing the TKIP in your router settings
and it should then connect..

thanks.

Thanks Hadaka but that didn't work; same "Association request to the driver failed" error in the logs.

The fact that I can no longer connect to the other (identical) router suggests that some global setting has perhaps been botched.

Any other ideas?

---

### Post by Hadaka on 2013-06-02
Hi, are you able to connect to any router using wired?
if yes then please do.
```
sudo apt-get update
sudo apt-get upgrade
```
also..if you havent already, go through
and delete all the 1,2,x extensions that are being generated on your ssid
and please post the output of..
```
lsmod
lspci -nnk | grep -iA3 net
```
and if possible create a new ssid without the "@" , i doubt it likes
```


zrtspshome@unifi
``` thanks

---

### Post by drblitzen on 2013-06-04
Yes I deleted the extraneously-listed entries. More info below:

lsmod
```

Module                  Size  Used by
nls_utf8               12557  1 
udf                    94575  1 
usbhid                 47199  0 
hid                    99592  1 usbhid
snd_hrtimer            12744  1 
dm_crypt               23125  1 
joydev                 17693  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec_hdmi     32474  1 
dell_laptop            18119  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dcdbas                 14490  1 dell_laptop
snd_hda_codec_idt      70795  1 
lib80211_crypt_tkip    17390  0 
snd_seq_midi           13324  0 
psmouse                97443  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_hda_intel          33773  5 
serio_raw              13211  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
intel_ips              18174  0 
wl                   3074856  0 
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
mei                    41616  0 
snd                    78855  21 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport_pc             32866  0 
mac_hid                13253  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
ext2                   73795  1 
radeon                804518  3 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
sdhci_pci              18826  0 
r8169                  62099  0 
sdhci                  33205  1 sdhci_pci
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   241921  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
wmi                    19256  1 dell_wmi
video                  19596  0

```


lspci -nnk | grep -iA3 net
```

04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
    Kernel modules: wl, bcma, brcmsmac
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Dell Device [1028:0413]
    Kernel driver in use: r8169
    Kernel modules: r8169

```

Also, I didn't notice last time that it's giving a new syslog error now after switching the router to CCMP-only, and appears to be trying to connect via IPv6 and failing:
```

Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> (eth1): device state change: config -> disconnected (reason 'none') [50 30 0]
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> (eth1): deactivating device (reason 'none') [0]
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Activation (eth1) starting connection 'zrtspshome@unifi'
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Activation (eth1/wireless): connection 'zrtspshome@unifi' has security, and secrets exist.  No new secrets needed.
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Config: added 'ssid' value 'zrtspshome@unifi'
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Config: added 'scan_ssid' value '1'
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Config: added 'auth_alg' value 'OPEN'
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Config: added 'psk' value '<omitted>'
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  4 20:48:46 bobstudio NetworkManager[932]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun  4 20:48:46 bobstudio NetworkManager[932]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun  4 20:48:46 bobstudio NetworkManager[932]: <info> Config: set interface ap_scan to 1
Jun  4 20:48:51 bobstudio wpa_supplicant[1348]: Trying to associate with cc:b2:55:d0:e4:36 (SSID='zrtspshome@unifi' freq=2417 MHz)
Jun  4 20:48:51 bobstudio NetworkManager[932]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  4 20:48:52 bobstudio wpa_supplicant[1348]: Associated with cc:b2:55:d0:e4:36
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Jun  4 20:48:52 bobstudio wpa_supplicant[1348]: WPA: Key negotiation completed with cc:b2:55:d0:e4:36 [PTK=CCMP GTK=CCMP]
Jun  4 20:48:52 bobstudio wpa_supplicant[1348]: CTRL-EVENT-CONNECTED - Connection to cc:b2:55:d0:e4:36 completed (reauth) [id=0 id_str=]
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> (eth1): supplicant interface state: 4-way handshake -> completed
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'zrtspshome@unifi'.
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> dhclient started with pid 22547
Jun  4 20:48:52 bobstudio dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jun  4 20:48:52 bobstudio dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jun  4 20:48:52 bobstudio dhclient: All rights reserved.
Jun  4 20:48:52 bobstudio dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  4 20:48:52 bobstudio dhclient: 
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> Activation (eth1) Beginning IP6 addrconf.
Jun  4 20:48:52 bobstudio avahi-daemon[944]: Withdrawing address record for fe80::72f1:a1ff:fefc:3dc3 on eth1.
Jun  4 20:48:52 bobstudio avahi-daemon[944]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fefc:3dc3.
Jun  4 20:48:52 bobstudio avahi-daemon[944]: Interface eth1.IPv6 no longer relevant for mDNS.
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jun  4 20:48:52 bobstudio NetworkManager[932]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Jun  4 20:48:52 bobstudio dhclient: Listening on LPF/eth1/70:f1:a1:fc:3d:c3
Jun  4 20:48:52 bobstudio dhclient: Sending on   LPF/eth1/70:f1:a1:fc:3d:c3
Jun  4 20:48:52 bobstudio dhclient: Sending on   Socket/fallback
Jun  4 20:48:52 bobstudio dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jun  4 20:48:53 bobstudio avahi-daemon[944]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fefc:3dc3.
Jun  4 20:48:53 bobstudio avahi-daemon[944]: New relevant interface eth1.IPv6 for mDNS.
Jun  4 20:48:53 bobstudio avahi-daemon[944]: Registering new address record for fe80::72f1:a1ff:fefc:3dc3 on eth1.*.
Jun  4 20:48:55 bobstudio dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jun  4 20:49:02 bobstudio dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
Jun  4 20:49:02 bobstudio kernel: [ 2141.889571] eth1: no IPv6 routers present
Jun  4 20:49:12 bobstudio NetworkManager[932]: <info> (eth1): IP6 addrconf timed out or failed.
Jun  4 20:49:12 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  4 20:49:12 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  4 20:49:12 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  4 20:49:23 bobstudio dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jun  4 20:49:34 bobstudio dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Jun  4 20:49:37 bobstudio NetworkManager[932]: <warn> (eth1): DHCPv4 request timed out.
Jun  4 20:49:37 bobstudio NetworkManager[932]: <info> (eth1): canceled DHCP transaction, DHCP client pid 22547
Jun  4 20:49:37 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jun  4 20:49:37 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jun  4 20:49:37 bobstudio NetworkManager[932]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jun  4 20:49:37 bobstudio NetworkManager[932]: <warn> Activation (eth1) failed for access point (zrtspshome@unifi)
Jun  4 20:49:37 bobstudio NetworkManager[932]: <warn> Activation (eth1) failed.
Jun  4 20:49:37 bobstudio NetworkManager[932]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jun  4 20:49:37 bobstudio NetworkManager[932]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun  4 20:49:37 bobstudio NetworkManager[932]: <info> (eth1): deactivating device (reason 'none') [0]
Jun  4 20:49:37 bobstudio avahi-daemon[944]: Withdrawing address record for fe80::72f1:a1ff:fefc:3dc3 on eth1.
Jun  4 20:49:37 bobstudio avahi-daemon[944]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fefc:3dc3.
Jun  4 20:49:37 bobstudio kernel: [ 2176.629568] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun  4 20:49:37 bobstudio kernel: [ 2176.629579] cfg80211: Restoring regulatory settings
Jun  4 20:49:37 bobstudio kernel: [ 2176.629587] cfg80211: Calling CRDA to update world regulatory domain
Jun  4 20:49:37 bobstudio avahi-daemon[944]: Interface eth1.IPv6 no longer relevant for mDNS.
Jun  4 20:49:37 bobstudio wpa_supplicant[1348]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  4 20:49:37 bobstudio NetworkManager[932]: <info> (eth1): supplicant interface state: completed -> disconnected
Jun  4 20:49:37 bobstudio kernel: [ 2176.638215] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638220] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638223] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638226] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638229] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638232] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638234] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638237] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638240] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638243] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638246] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638249] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638251] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638254] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638256] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638259] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638262] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638265] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638268] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638271] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638273] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638276] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638279] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638282] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638285] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638288] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638291] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638294] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638297] cfg80211: Disabling freq 5170 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638299] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638302] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638305] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638308] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638310] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638313] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638316] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638319] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638322] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638325] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638328] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638331] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638333] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638336] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638339] cfg80211: Disabling freq 5260 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638340] cfg80211: Disabling freq 5280 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638342] cfg80211: Disabling freq 5300 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638344] cfg80211: Disabling freq 5320 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638346] cfg80211: Disabling freq 5500 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638348] cfg80211: Disabling freq 5520 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638350] cfg80211: Disabling freq 5540 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638351] cfg80211: Disabling freq 5560 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638353] cfg80211: Disabling freq 5580 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638355] cfg80211: Disabling freq 5600 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638356] cfg80211: Disabling freq 5620 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638358] cfg80211: Disabling freq 5640 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638360] cfg80211: Disabling freq 5660 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638361] cfg80211: Disabling freq 5680 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638363] cfg80211: Disabling freq 5700 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638365] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638368] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638371] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638374] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638377] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638380] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638383] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638386] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638388] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638391] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638393] cfg80211: Disabling freq 5920 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638394] cfg80211: Disabling freq 5940 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638396] cfg80211: Disabling freq 5960 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638397] cfg80211: Disabling freq 5980 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638399] cfg80211: Disabling freq 6000 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638400] cfg80211: Disabling freq 6020 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638402] cfg80211: Disabling freq 6040 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638403] cfg80211: Disabling freq 6060 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638405] cfg80211: Disabling freq 6080 MHz
Jun  4 20:49:37 bobstudio kernel: [ 2176.638409] cfg80211: World regulatory domain updated:
Jun  4 20:49:37 bobstudio kernel: [ 2176.638411] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638414] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638416] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638419] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638421] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:37 bobstudio kernel: [ 2176.638423] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 20:49:38 bobstudio avahi-daemon[944]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fefc:3dc3.
Jun  4 20:49:38 bobstudio avahi-daemon[944]: New relevant interface eth1.IPv6 for mDNS.
Jun  4 20:49:38 bobstudio avahi-daemon[944]: Registering new address record for fe80::72f1:a1ff:fefc:3dc3 on eth1.*.

```

Perhaps a setting got switched to tell it to connect via IPv6-only? Not finding such a setting with Google.

---

### Post by Hadaka on 2013-06-05
Hi, is suspect having 3 different drivers showing up in your
wireless card may be part of the problem.
please post the output of..
```
cat /etc/modules
```
thanks.

---

### Post by drblitzen on 2013-06-06
cat /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```

I've also tethered to my cell phone and done a full apt-get update, upgrade and dist-upgrade to no avail. Not sure how what all it did since "lsb_release -d" still yields 12.04.2.

---

