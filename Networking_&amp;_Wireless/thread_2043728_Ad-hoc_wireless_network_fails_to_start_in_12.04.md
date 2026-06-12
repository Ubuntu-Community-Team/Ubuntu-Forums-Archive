---
title: "Ad-hoc wireless network fails to start in 12.04"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by audwan on 2012-08-17
I've tried to create an ad-hoc wireless network on my Ubuntu 12.04 machine using this guide (NetworkManager method):
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

When I try to connect to the hidden network using Network Manager, the wireless symbol just rolls for a minute and then the connection attempt fails. If I try again it fails immidiately, so I need to restart Network Manager or reboot to try again.

I've tried setting a static IP and shared under IPv4 both, to no avail.

Below are some logs and stuff that might be useful. I appreciate any help.

```
$ sudo lshw -class network
.
.
.
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 8c:70:5a:00:c3:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-29-generic firmware=17.168.5.3 build 42301 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:e6600000-e6601fff

```


```
$ iw list | grep "Supported interface modes" --after-context=5
	Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * monitor
```

First attempt to connect:

```
$ cat /var/log/syslog
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Activation (wlan0/wireless): connection 'Hotspot' has security, and secrets exist.  No new secrets needed.
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Config: added 'ssid' value 'hikt6675'
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Config: added 'mode' value '1'
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Config: added 'frequency' value '2412'
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Config: added 'key_mgmt' value 'NONE'
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Config: added 'wep_key0' value '<omitted>'
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Config: added 'wep_tx_keyidx' value '0'
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> Config: set interface ap_scan to 2
Aug 17 12:49:47 hikt6675 wpa_supplicant[1257]: Trying to associate with SSID 'hikt6675'
Aug 17 12:49:47 hikt6675 wpa_supplicant[1257]: Could not set interface wlan0 flags: Device or resource busy
Aug 17 12:49:47 hikt6675 wpa_supplicant[1257]: nl80211: Failed to set interface into IBSS mode
Aug 17 12:49:47 hikt6675 wpa_supplicant[1257]: Association request to the driver failed
Aug 17 12:49:47 hikt6675 NetworkManager[5514]: <info> (wlan0): supplicant interface state: inactive -> associating
Aug 17 12:49:57 hikt6675 wpa_supplicant[1257]: Authentication with 00:00:00:00:00:00 timed out.
Aug 17 12:49:57 hikt6675 wpa_supplicant[1257]: Trying to associate with SSID 'hikt6675'
Aug 17 12:49:57 hikt6675 wpa_supplicant[1257]: Association request to the driver failed
Aug 17 12:50:07 hikt6675 wpa_supplicant[1257]: Authentication with 00:00:00:00:00:00 timed out.
Aug 17 12:50:07 hikt6675 wpa_supplicant[1257]: Trying to associate with SSID 'hikt6675'
Aug 17 12:50:07 hikt6675 wpa_supplicant[1257]: Association request to the driver failed
Aug 17 12:50:17 hikt6675 wpa_supplicant[1257]: Authentication with 00:00:00:00:00:00 timed out.
Aug 17 12:50:17 hikt6675 wpa_supplicant[1257]: Trying to associate with SSID 'hikt6675'
Aug 17 12:50:17 hikt6675 wpa_supplicant[1257]: Association request to the driver failed
Aug 17 12:50:27 hikt6675 wpa_supplicant[1257]: Authentication with 00:00:00:00:00:00 timed out.
Aug 17 12:50:27 hikt6675 wpa_supplicant[1257]: Trying to associate with SSID 'hikt6675'
Aug 17 12:50:27 hikt6675 wpa_supplicant[1257]: Association request to the driver failed
Aug 17 12:50:37 hikt6675 wpa_supplicant[1257]: Authentication with 00:00:00:00:00:00 timed out.
Aug 17 12:50:37 hikt6675 wpa_supplicant[1257]: Trying to associate with SSID 'hikt6675'
Aug 17 12:50:37 hikt6675 wpa_supplicant[1257]: Association request to the driver failed
Aug 17 12:50:47 hikt6675 wpa_supplicant[1257]: Authentication with 00:00:00:00:00:00 timed out.
Aug 17 12:50:47 hikt6675 wpa_supplicant[1257]: Trying to associate with SSID 'hikt6675'
Aug 17 12:50:47 hikt6675 wpa_supplicant[1257]: Association request to the driver failed
Aug 17 12:50:47 hikt6675 NetworkManager[5514]: <warn> Activation (wlan0/wireless): Ad-Hoc network creation took too long, failing activation.
Aug 17 12:50:47 hikt6675 NetworkManager[5514]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Aug 17 12:50:47 hikt6675 NetworkManager[5514]: <warn> Activation (wlan0) failed for access point (hikt6675)
Aug 17 12:50:47 hikt6675 NetworkManager[5514]: <warn> Activation (wlan0) failed.
Aug 17 12:50:47 hikt6675 NetworkManager[5514]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 17 12:50:47 hikt6675 NetworkManager[5514]: <info> (wlan0): deactivating device (reason 'none') [0]
```

Second attempt to connect:

```
$ cat /var/log/syslog
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) starting connection 'Hotspot'
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> (wlan0): bringing up device.
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> (wlan0): device state change: config -> failed (reason 'config-failed') [50 120 4]
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <warn> Activation (wlan0) failed for access point (hikt6675)
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <warn> Activation (wlan0) failed.
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 17 13:01:20 hikt6675 NetworkManager[5514]: <info> (wlan0): deactivating device (reason 'none') [0]

```

---

