---
title: "PCI WiFi and Video drivers problem"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by hippotimr on 2011-06-15
Hi everybody,

I'm a Linux newbie, though I installed Ubuntu on few laptops already and solved few WiFi problems thanks to the existing treads. This one's just too much for me at the time.

So there is a new pc system with pci wlan card Level One WNC 0301 on Realtek 8185, I installed x64 Ubuntu 11.04 and it recognizes the wlan card, wifi works for some time and then stops working after I install nvidia drivers (sometimes after installing these and then 2nd reboot). The networks are still visible, but I can't connect - get the same auth message over and over. The same problem was on win7 (dual boot on it's own partition), solved with newer drivers.

What have I tried so far:
- reboot the router, reboot the system
- change whatever I could change in wifi settings
- install the drivers that worked on win7 with ndiswrapper - made it worse, device present but wifi disappears and doesn't work at all, the same with xp driver
- reinstall ubuntu and try to do everything slowly (that's when I figured out the drivers/wifi dependence)
- graphics failsafe mode, that's where I am now, video drivers are disabled and wifi works

So my guess it has something to do with IRQ conflict, but I just don't have enough linux knowledge/experience to solve this on my own.

The drivers are "nvidia accelerated graphics driver (version current)"

Here is some output.

sudo lshw -C network
```
*-network              
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 20
       serial: 00:11:6b:65:18:77
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.83 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 ioport:d000(size=256) memory:fb200000-fb2003ff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 6c:62:6d:ee:10:f0
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:c000(size=256) memory:da104000-da104fff memory:da100000-da103fff

```syslog
```
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) starting connection 'Auto INET'
Jun 15 11:14:01 hippo NetworkManager[756]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 15 11:14:01 hippo NetworkManager[756]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0/wireless): access point 'Auto INET' has security, but secrets are required.
Jun 15 11:14:01 hippo NetworkManager[756]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 15 11:14:01 hippo rtkit-daemon[1362]: Successfully made thread 1575 of process 1575 (n/a) owned by '1000' high priority at nice level -11.
Jun 15 11:14:01 hippo rtkit-daemon[1362]: Supervising 9 threads of 3 processes of 2 users.
Jun 15 11:14:01 hippo pulseaudio[1575]: pid.c: Daemon already running.
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 15 11:14:01 hippo NetworkManager[756]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 15 11:14:01 hippo NetworkManager[756]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0/wireless): connection 'Auto INET' has security, and secrets exist.  No new secrets needed.
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Config: added 'ssid' value 'INET'
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Config: added 'scan_ssid' value '1'
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Config: added 'psk' value '<omitted>'
Jun 15 11:14:01 hippo NetworkManager[756]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 15 11:14:01 hippo NetworkManager[756]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 15 11:14:01 hippo NetworkManager[756]: <info> Config: set interface ap_scan to 1
Jun 15 11:14:01 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jun 15 11:14:03 hippo wpa_supplicant[957]: Trying to associate with 00:1c:33:26:71:be (SSID='INET' freq=2427 MHz)
Jun 15 11:14:03 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 15 11:14:03 hippo kernel: [  103.049007] wlan0: authenticate with 00:1c:33:26:71:be (try 1)
Jun 15 11:14:03 hippo kernel: [  103.248421] wlan0: authenticate with 00:1c:33:26:71:be (try 2)
Jun 15 11:14:04 hippo kernel: [  103.447878] wlan0: authenticate with 00:1c:33:26:71:be (try 3)
Jun 15 11:14:04 hippo kernel: [  103.647306] wlan0: authentication with 00:1c:33:26:71:be timed out
Jun 15 11:14:13 hippo wpa_supplicant[957]: Authentication with 00:1c:33:26:71:be timed out.
Jun 15 11:14:13 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 15 11:14:13 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 15 11:14:15 hippo wpa_supplicant[957]: Trying to associate with 00:1c:33:26:71:be (SSID='INET' freq=2427 MHz)
Jun 15 11:14:15 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 15 11:14:15 hippo kernel: [  115.194286] wlan0: direct probe to 00:1c:33:26:71:be (try 1/3)
Jun 15 11:14:15 hippo kernel: [  115.393728] wlan0: direct probe to 00:1c:33:26:71:be (try 2/3)
Jun 15 11:14:16 hippo kernel: [  115.593176] wlan0: direct probe to 00:1c:33:26:71:be (try 3/3)
Jun 15 11:14:16 hippo kernel: [  115.792593] wlan0: direct probe to 00:1c:33:26:71:be timed out
Jun 15 11:14:25 hippo wpa_supplicant[957]: Authentication with 00:1c:33:26:71:be timed out.
Jun 15 11:14:25 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 15 11:14:25 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 15 11:14:27 hippo wpa_supplicant[957]: Trying to associate with 00:1c:33:26:71:be (SSID='INET' freq=2427 MHz)
Jun 15 11:14:27 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 15 11:14:27 hippo kernel: [  127.339567] wlan0: direct probe to 00:1c:33:26:71:be (try 1/3)
Jun 15 11:14:28 hippo kernel: [  127.538984] wlan0: direct probe to 00:1c:33:26:71:be (try 2/3)
Jun 15 11:14:28 hippo kernel: [  127.738404] wlan0: direct probe to 00:1c:33:26:71:be (try 3/3)
Jun 15 11:14:28 hippo kernel: [  127.937831] wlan0: direct probe to 00:1c:33:26:71:be timed out
Jun 15 11:14:37 hippo wpa_supplicant[957]: Authentication with 00:1c:33:26:71:be timed out.
Jun 15 11:14:37 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 15 11:14:37 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 15 11:14:39 hippo wpa_supplicant[957]: Trying to associate with 00:1c:33:26:71:be (SSID='INET' freq=2427 MHz)
Jun 15 11:14:39 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 15 11:14:40 hippo kernel: [  139.484823] wlan0: direct probe to 00:1c:33:26:71:be (try 1/3)
Jun 15 11:14:40 hippo kernel: [  139.684274] wlan0: direct probe to 00:1c:33:26:71:be (try 2/3)
Jun 15 11:14:40 hippo kernel: [  139.883670] wlan0: direct probe to 00:1c:33:26:71:be (try 3/3)
Jun 15 11:14:40 hippo kernel: [  140.083097] wlan0: direct probe to 00:1c:33:26:71:be timed out
Jun 15 11:14:43 hippo NetworkManager[756]: <warn> (wlan0): link timed out.
Jun 15 11:14:50 hippo wpa_supplicant[957]: Authentication with 00:1c:33:26:71:be timed out.
Jun 15 11:14:50 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 15 11:14:50 hippo NetworkManager[756]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
```The probe/timeout stage is then repeated. Please help, I try to use this computer to work and the wifi problem makes it impossible :(

---

