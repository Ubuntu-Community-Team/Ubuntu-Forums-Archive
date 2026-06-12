---
title: "Network Manager Won't Accept Correct Wireless Key!"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by Maleificus on 2013-04-21
I am running a Sony Vaio VGN-FW140E with Ubuntu 12.10. I have been having an issue since the install of Ubuntu to the system. When I attempt to connect to my home wireless network (or any, I even attempted to use my phone as a wireless hotspot) it will ask as per usual for the Wireless Key. I enter the wireless key and the network manager attempts to connect. Then it asks for the wireless key again. This cycle continues and there is no way for me to access the internet through the wireless on the laptop. Currently I am using my phone's USB tethering ability but this is not sufficient due to needing my phone to be available if I have downloads running and leaving the home. I have three Androids connected to the wireless and I have checked and rechecked the key so I know that the wireless IS working and I DO have the correct key. Thanks in advance guys!

---

### Post by ahallubuntu on 2013-04-21
~

---

### Post by Maleificus on 2013-04-21
>                 
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:4c:18:34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-27-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:d1900000-d1901fff
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 13
       serial: 00:1d:ba:1c:d2:87
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d0520000-d0523fff ioport:2000(size=256) memory:d0500000-d051ffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: a6:67:ed:50:0a:e7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.127 link=yes multicast=yes

That is the ouput received.

---

### Post by Maleificus on 2013-04-21
Bump

---

### Post by Maleificus on 2013-04-22
Update!

I followed some steps in other forums that I researched given the fact that I was not receiving help here and now it's not even asking for the password again but won't connect...

---

### Post by steeldriver on 2013-04-22
What steps did you follow exactly?

Repeated re-auth requests with Intel wifi cards are often due to a bug in the iwlwifi driver related to wireless-n mode - you can usually work around that by disabling 11n when the kernel module is loaded

---

### Post by Maleificus on 2013-04-22
[http://ubuntuforums.org/showthread.php?t=1970820](http://ubuntuforums.org/showthread.php?t=1970820)

[http://askubuntu.com/questions/261988/no-longer-able-to-use-wifi-adapter-intel-wifi-link-5100-ubuntu-12-04](http://askubuntu.com/questions/261988/no-longer-able-to-use-wifi-adapter-intel-wifi-link-5100-ubuntu-12-04)

This was given to me on #ubuntu at freenode. I asked for help and I was told to try these. This is what rendered my card into the action it is taking now, it isn't asking for the key repeatedly but it is also refusing to connect as before.

---

### Post by Maleificus on 2013-04-23
UPDATE!: It is obvious that I messed something up trying to fix the issue, working on a fresh install now and still facing the issue where it is refusing to accept the key and keeps asking for it. How do I fix this based on what you said previously?

---

### Post by steeldriver on 2013-04-23
Open a terminal and try

```

sudo modprobe -r iwlwifi

sudo modprobe -v iwlwifi 11n_disable=1
```

If that seems to do the trick, you can make it persistent by creating a modprobe file entry by doing

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

---

### Post by Maleificus on 2013-04-23
Unless I'm supposed to restart after entering the first set of commands then it doesn't work. No changes.

---

### Post by steeldriver on 2013-04-23
Hmm... then it may be above my paygrade. Let's have a look in in the dmesg log to see if there are any obvious error messages:

```
dmesg | grep '\<wlan'
```

---

### Post by Maleificus on 2013-04-23
> [   17.945914] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.946847] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

That is the output I received.

---

### Post by steeldriver on 2013-04-23
Not much to work with there - how about syslog?

```
grep '\<wlan' /var/log/syslog
```

---

### Post by Maleificus on 2013-04-23
> 66:fd (try 1/3)
Apr 23 11:49:04 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 11:49:05 Luisa kernel: [ 2508.164035] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 11:49:05 Luisa kernel: [ 2508.368032] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 11:49:05 Luisa kernel: [ 2508.572040] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 11:49:05 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 11:49:05 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 11:49:10 Luisa NetworkManager[853]: <warn> Activation (wlan0/wireless): association took too long.
Apr 23 11:49:10 Luisa NetworkManager[853]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 23 11:49:10 Luisa NetworkManager[853]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr 23 11:49:10 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Apr 23 11:51:11 Luisa NetworkManager[853]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Apr 23 11:51:11 Luisa NetworkManager[853]: <warn> Activation (wlan0) failed for connection 'jasnet'
Apr 23 11:51:11 Luisa NetworkManager[853]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 23 11:51:11 Luisa NetworkManager[853]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) starting connection 'jasnet'
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0/wireless): access point 'jasnet' has security, but secrets are required.
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0/wireless): connection 'jasnet' has security, and secrets exist.  No new secrets needed.
Apr 23 11:56:10 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 11:56:11 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 11:56:22 Luisa wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 11:56:22 Luisa kernel: [ 2945.308257] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 11:56:22 Luisa kernel: [ 2945.318207] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 11:56:22 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 11:56:22 Luisa kernel: [ 2945.520034] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 11:56:22 Luisa kernel: [ 2945.724094] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 11:56:22 Luisa kernel: [ 2945.928065] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 11:56:22 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 11:56:23 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 11:56:26 Luisa wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 11:56:26 Luisa kernel: [ 2949.178066] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 11:56:26 Luisa kernel: [ 2949.179614] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 11:56:26 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 11:56:26 Luisa kernel: [ 2949.380014] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 11:56:26 Luisa kernel: [ 2949.584026] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 11:56:26 Luisa kernel: [ 2949.788018] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 11:56:26 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 11:56:26 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 11:56:30 Luisa wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 11:56:30 Luisa kernel: [ 2953.092696] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 11:56:30 Luisa kernel: [ 2953.094187] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 11:56:30 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 11:56:30 Luisa kernel: [ 2953.296038] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 11:56:30 Luisa kernel: [ 2953.500041] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 11:56:30 Luisa kernel: [ 2953.704068] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 11:56:30 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 11:56:30 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 11:56:33 Luisa wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 11:56:33 Luisa kernel: [ 2956.975506] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 11:56:33 Luisa kernel: [ 2956.976951] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 11:56:33 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 11:56:34 Luisa kernel: [ 2957.180016] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 11:56:34 Luisa kernel: [ 2957.384047] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 11:56:34 Luisa kernel: [ 2957.588047] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 11:56:34 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 11:56:34 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 11:56:35 Luisa NetworkManager[853]: <warn> Activation (wlan0/wireless): association took too long.
Apr 23 11:56:35 Luisa NetworkManager[853]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 23 11:56:35 Luisa NetworkManager[853]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr 23 11:56:35 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Apr 23 11:56:42 Luisa NetworkManager[853]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Apr 23 11:56:42 Luisa NetworkManager[853]: <warn> Activation (wlan0) failed for connection 'jasnet'
Apr 23 11:56:42 Luisa NetworkManager[853]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 23 11:56:42 Luisa NetworkManager[853]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) starting connection 'jasnet'
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0/wireless): access point 'jasnet' has security, but secrets are required.
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0/wireless): connection 'jasnet' has security, and secrets exist.  No new secrets needed.
Apr 23 12:01:42 Luisa NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 12:01:43 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:01:46 Luisa wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:01:46 Luisa kernel: [ 3269.174859] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:01:46 Luisa kernel: [ 3269.179880] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:01:46 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:01:46 Luisa kernel: [ 3269.380014] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:01:46 Luisa kernel: [ 3269.584015] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:01:46 Luisa kernel: [ 3269.788015] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:01:46 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:01:46 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:01:58 Luisa wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:01:58 Luisa kernel: [ 3281.262168] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:01:58 Luisa kernel: [ 3281.263666] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:01:58 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:01:58 Luisa kernel: [ 3281.464035] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:01:58 Luisa kernel: [ 3281.668033] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:01:58 Luisa kernel: [ 3281.872016] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:01:58 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:01:58 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:02:02 Luisa wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:02:02 Luisa kernel: [ 3285.174895] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:02:02 Luisa kernel: [ 3285.179003] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:02:02 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:02:02 Luisa kernel: [ 3285.380034] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:02:02 Luisa kernel: [ 3285.584022] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:02:02 Luisa kernel: [ 3285.788033] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:02:02 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:02:02 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:02:07 Luisa NetworkManager[853]: <warn> Activation (wlan0/wireless): association took too long.
Apr 23 12:02:07 Luisa NetworkManager[853]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 23 12:02:07 Luisa NetworkManager[853]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr 23 12:02:07 Luisa NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Apr 23 12:02:13 Luisa NetworkManager[853]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Apr 23 12:02:13 Luisa NetworkManager[853]: <warn> Activation (wlan0) failed for connection 'jasnet'
Apr 23 12:02:13 Luisa NetworkManager[853]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 23 12:02:13 Luisa NetworkManager[853]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 23 12:03:10 Luisa NetworkManager[863]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/net/wlan0, iface: wlan0)
Apr 23 12:03:10 Luisa NetworkManager[863]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 23 12:03:10 Luisa NetworkManager[863]: <info> (wlan0): using nl80211 for WiFi device control
Apr 23 12:03:10 Luisa NetworkManager[863]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 4)
Apr 23 12:03:10 Luisa NetworkManager[863]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 23 12:03:10 Luisa NetworkManager[863]: <info> (wlan0): now managed
Apr 23 12:03:10 Luisa NetworkManager[863]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 23 12:03:10 Luisa NetworkManager[863]: <info> (wlan0): bringing up device.
Apr 23 12:03:10 Luisa NetworkManager[863]: <info> (wlan0): preparing device.
Apr 23 12:03:10 Luisa NetworkManager[863]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 23 12:03:10 Luisa kernel: [   15.050776] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 23 12:03:10 Luisa kernel: [   15.051865] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 23 12:03:11 Luisa NetworkManager[863]: <info> (wlan0) supports 5 scan SSIDs
Apr 23 12:03:11 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 23 12:03:11 Luisa NetworkManager[863]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 23 12:03:11 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: ready -> inactive
Apr 23 12:03:11 Luisa NetworkManager[863]: <info> (wlan0) supports 5 scan SSIDs
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> Activation (wlan0) starting connection 'jasnet'
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> Activation (wlan0/wireless): connection 'jasnet' has security, and secrets exist.  No new secrets needed.
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 12:03:14 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 23 12:03:17 Luisa wpa_supplicant[1005]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:03:17 Luisa kernel: [   21.694487] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:03:17 Luisa kernel: [   21.706610] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:03:17 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:03:17 Luisa kernel: [   21.908012] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:03:17 Luisa kernel: [   22.112033] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:03:18 Luisa kernel: [   22.316033] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:03:18 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:03:18 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:03:29 Luisa wpa_supplicant[1005]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:03:29 Luisa kernel: [   33.569278] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:03:29 Luisa kernel: [   33.570403] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:03:29 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:03:29 Luisa kernel: [   33.772035] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:03:29 Luisa kernel: [   33.976033] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:03:30 Luisa kernel: [   34.180031] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:03:30 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:03:30 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:03:33 Luisa wpa_supplicant[1005]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:03:33 Luisa kernel: [   37.458059] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:03:33 Luisa kernel: [   37.460058] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:03:33 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:03:33 Luisa kernel: [   37.664013] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:03:33 Luisa kernel: [   37.868032] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:03:33 Luisa kernel: [   38.072034] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:03:33 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:03:34 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:03:37 Luisa wpa_supplicant[1005]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:03:37 Luisa kernel: [   41.347442] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:03:37 Luisa kernel: [   41.354453] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:03:37 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:03:37 Luisa kernel: [   41.556030] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:03:37 Luisa kernel: [   41.760028] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:03:37 Luisa kernel: [   41.964030] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:03:37 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:03:37 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:03:39 Luisa NetworkManager[863]: <warn> Activation (wlan0/wireless): association took too long.
Apr 23 12:03:39 Luisa NetworkManager[863]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 23 12:03:39 Luisa NetworkManager[863]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr 23 12:03:39 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> Activation (wlan0/wireless): connection 'jasnet' has security, and secrets exist.  No new secrets needed.
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 12:04:06 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:04:09 Luisa wpa_supplicant[1005]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:04:09 Luisa kernel: [   73.609701] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:04:09 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:04:09 Luisa kernel: [   73.621991] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:04:09 Luisa kernel: [   73.824033] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:04:09 Luisa kernel: [   74.028036] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:04:10 Luisa kernel: [   74.232052] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:04:10 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:04:10 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:04:13 Luisa wpa_supplicant[1005]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:04:13 Luisa kernel: [   77.479040] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:04:13 Luisa kernel: [   77.480325] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:04:13 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:04:13 Luisa kernel: [   77.684060] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:04:13 Luisa kernel: [   77.888039] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:04:13 Luisa kernel: [   78.092055] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:04:13 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:04:14 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:04:17 Luisa wpa_supplicant[1005]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:04:17 Luisa kernel: [   81.364214] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:04:17 Luisa kernel: [   81.366979] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:04:17 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:04:17 Luisa kernel: [   81.568048] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:04:17 Luisa kernel: [   81.772051] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:04:17 Luisa kernel: [   81.976039] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:04:17 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:04:17 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:04:21 Luisa wpa_supplicant[1005]: wlan0: SME: Trying to authenticate with 4c:60:de:a6:66:fd (SSID='jasnet' freq=2462 MHz)
Apr 23 12:04:21 Luisa kernel: [   85.265122] wlan0: authenticate with 4c:60:de:a6:66:fd
Apr 23 12:04:21 Luisa kernel: [   85.266023] wlan0: direct probe to 4c:60:de:a6:66:fd (try 1/3)
Apr 23 12:04:21 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 23 12:04:21 Luisa kernel: [   85.468051] wlan0: direct probe to 4c:60:de:a6:66:fd (try 2/3)
Apr 23 12:04:21 Luisa kernel: [   85.672021] wlan0: direct probe to 4c:60:de:a6:66:fd (try 3/3)
Apr 23 12:04:21 Luisa kernel: [   85.876011] wlan0: authentication with 4c:60:de:a6:66:fd timed out
Apr 23 12:04:21 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 23 12:04:21 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 12:04:31 Luisa NetworkManager[863]: <warn> Activation (wlan0/wireless): association took too long.
Apr 23 12:04:31 Luisa NetworkManager[863]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 23 12:04:31 Luisa NetworkManager[863]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr 23 12:04:31 Luisa NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Apr 23 12:04:44 Luisa NetworkManager[863]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Apr 23 12:04:44 Luisa NetworkManager[863]: <warn> Activation (wlan0) failed for connection 'jasnet'
Apr 23 12:04:44 Luisa NetworkManager[863]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 23 12:04:44 Luisa NetworkManager[863]: <info> (wlan0): deactivating device (reason 'none') [0]



There was more before it but it was truncated.

---

### Post by Maleificus on 2013-04-25
Bump

---

### Post by steeldriver on 2013-04-25
Well I'm just about out of ideas - there's one more known issue with a bunch of Intel cards that we can check for:

```
grep CALIB /var/log/kern.log
```

(you can check for the same CALIB string in /var/log/syslog as well, but kern.log seems to get rotated a bit less)

---

### Post by Maleificus on 2013-04-25
> Apr 23 11:07:28 Luisa kernel: [   11.189622] iwlwifi 0000:05:00.0: >device EEPROM VER=0x11f, CALIB=0x4
Apr 23 11:12:56 Luisa kernel: [  339.237665] iwlwifi 0000:05:00.0: >device EEPROM VER=0x11f, CALIB=0x4
Apr 23 12:03:05 Luisa kernel: [    9.764402] iwlwifi 0000:05:00.0: device EEPROM VER=0x11f, CALIB=0x4
Apr 24 09:32:35 Luisa kernel: [   11.972972] iwlwifi 0000:05:00.0: device EEPROM VER=0x11f, CALIB=0x4
Apr 24 20:39:04 Luisa kernel: [   12.629939] iwlwifi 0000:05:00.0: device EEPROM VER=0x11f, CALIB=0x4



Here ya go!

---

