---
title: "EDimax EW-7811Un Wireless not working"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by RaTTuS- on 2011-11-10
**1 ) Machine Brand and Model (PC/Laptop)**:
```
Foxcom 8GB silent miniitx home built machine
```[B]2 ) Wireless Brand, Model and Wireless Chipset:

[/B]```
Bus 001 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

```[B]3 ) check interface:
[/B]```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

```[B]4 ) Check for modules:
[/B]```
lsmod | grep 8192
rtl8192cu             103210  0 
rtl8192c_common        75767  1 rtl8192cu
rtlwifi               110972  1 rtl8192cu
mac80211              310872  3 rtl8192cu,rtl8192c_common,rtlwifi

```[B]5 ) Kernel boot messages
[/B]```
[70271.382802] rtl8192cu: MAC address: 80:1f:02:10:30:97
[70271.382823] rtl8192cu: Board Type 0
[70271.391428] rtl8192cu: rx_max_size 15360, rx_urb_num 8, in_ep 1
[70271.733882] rtl8192cu: MAC auto ON okay!
[70271.768757] rtl8192cu: Tx queue select: 0x05
[70271.769549] rtl8192c: Loading firmware file rtlwifi/rtl8192cufw.bin
[70397.224132] rtl8192cu: MAC address: 80:1f:02:10:30:97
[70397.224156] rtl8192cu: Board Type 0
[70397.235373] rtl8192cu: rx_max_size 15360, rx_urb_num 8, in_ep 1
[70397.547972] rtl8192cu: MAC auto ON okay!
[70397.581586] rtl8192cu: Tx queue select: 0x05
[70397.583531] rtl8192c: Loading firmware file rtlwifi/rtl8192cufw.bin

```[B]6 ) Network configuration
[/B]```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: d0:27:88:65:22:13
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:40 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 80:1f:02:10:30:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

```[B]8 ) Ubuntu Version: 
[/B]```
lsb_release -d
Description:    Ubuntu 11.10

```[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]```
uname -mr
3.0.0-12-generic x86_64

```starting wireless scan
```
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0/wireless): access point 'DogHouse' has security, but secrets are required.
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0/wireless): connection 'DogHouse' has security, and secrets exist.  No new secrets needed.
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Config: added 'ssid' value 'DogHouse'
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Config: added 'scan_ssid' value '1'
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Config: added 'psk' value '<omitted>'
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> Config: set interface ap_scan to 1
Nov 10 16:47:02 BlackBox NetworkManager[855]: <info> (wlan0): supplicant interface state: disconnected -> scanning

```auto box pops up and asks for the password - which is correct
```

Nov 10 16:48:03 BlackBox NetworkManager[855]: <warn> Activation (wlan0/wireless): association took too long.
Nov 10 16:48:03 BlackBox NetworkManager[855]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 10 16:48:03 BlackBox NetworkManager[855]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 10 16:48:03 BlackBox NetworkManager[855]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 10 16:48:03 BlackBox NetworkManager[855]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 10 16:48:06 BlackBox NetworkManager[855]: <info> (wlan0): supplicant interface state: scanning -> inactive
Nov 10 16:48:11 BlackBox NetworkManager[855]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Activation (wlan0/wireless): connection 'DogHouse' has security, and secrets exist.  No new secrets needed.
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Config: added 'ssid' value 'DogHouse'
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Config: added 'scan_ssid' value '1'
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Config: added 'psk' value '<omitted>'
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> Config: set interface ap_scan to 1
Nov 10 16:48:12 BlackBox NetworkManager[855]: <info> (wlan0): supplicant interface state: inactive -> scanning



```I've tried [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax#USB)
and
[http://ubuntuforums.org/showthread.php?t=1744371&highlight=EDimax+EW-7811Un](http://ubuntuforums.org/showthread.php?t=1744371&highlight=EDimax+EW-7811Un)
and
[http://ubuntuforums.org/showpost.php?p=10950599&postcount=26](http://ubuntuforums.org/showpost.php?p=10950599&postcount=26)

compiled / fixed errors / installed - rebooted to no avail - it sees and talks but does not connect:confused: any other hints I'd be grateful for .

---

