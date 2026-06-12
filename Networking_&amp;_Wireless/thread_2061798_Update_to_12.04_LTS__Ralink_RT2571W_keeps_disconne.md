---
title: "Update to 12.04 LTS : Ralink RT2571W keeps disconnecting"
date: 2012-09-23
forum: Networking &amp; Wireless
---

### Post by brazzmonkey on 2012-09-23
Hi there,

I recently upgraded to 12.04 (Kubuntu). Now my wireless keeps disconnecting every now and then. When this happens, I am asked to type network password, but it then fails to reconnect.
The only way I found to get it reconnected is to disable networking in NetworkManager and re-enable it.

I have a Ralink RT2571W USB dongle. I tried to activate software encryption, but then it won't connect.

It used to work fine with previous LTS.

In case it helps, here is the outpout of syslog :
```
Sep 23 17:49:39 localhost kernel: [ 4361.912677] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 23 17:49:40 localhost NetworkManager[966]: <info> (wlan0): bringing up device.
Sep 23 17:49:40 localhost NetworkManager[966]: <info> WiFi hardware radio set enabled
Sep 23 17:49:40 localhost NetworkManager[966]: <info> WiFi now enabled by radio killswitch
Sep 23 17:49:40 localhost NetworkManager[966]: <info> (wlan0): bringing up device.
Sep 23 17:49:40 localhost kernel: [ 4362.685187] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 23 17:49:40 localhost NetworkManager[966]: <info> (wlan0): supplicant interface state: starting -> ready
Sep 23 17:49:40 localhost NetworkManager[966]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Sep 23 17:49:40 localhost NetworkManager[966]: <info> (wlan0): supplicant interface state: ready -> inactive
Sep 23 17:49:40 localhost NetworkManager[966]: <warn> Trying to remove a non-existant call id.
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Auto-activating connection 'VIRUS'.
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) starting connection 'VIRUS'
Sep 23 17:49:42 localhost NetworkManager[966]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 23 17:49:42 localhost NetworkManager[966]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 23 17:49:42 localhost NetworkManager[966]: <info> (wlan0): preparing device.
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0/wireless): access point 'VIRUS' has security, but secrets are required.
Sep 23 17:49:42 localhost NetworkManager[966]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 23 17:49:42 localhost NetworkManager[966]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 23 17:49:42 localhost NetworkManager[966]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0/wireless): connection 'VIRUS' has security, and secrets exist.  No new secrets needed.
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Config: added 'ssid' value 'VIRUS'
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Config: added 'scan_ssid' value '1'
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Config: added 'bssid' value '00:09:5b:9c:69:5a'
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Config: added 'psk' value '<omitted>'
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 23 17:49:42 localhost NetworkManager[966]: <info> Config: set interface ap_scan to 1
Sep 23 17:49:42 localhost NetworkManager[966]: <info> (wlan0): supplicant interface state: inactive -> scanning
Sep 23 17:49:43 localhost wpa_supplicant[1043]: Trying to authenticate with 00:09:5b:9c:69:5a (SSID='VIRUS' freq=2462 MHz)
Sep 23 17:49:43 localhost NetworkManager[966]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 23 17:49:43 localhost kernel: [ 4366.055395] wlan0: authenticate with 00:09:5b:9c:69:5a (try 1)
Sep 23 17:49:43 localhost wpa_supplicant[1043]: Trying to associate with 00:09:5b:9c:69:5a (SSID='VIRUS' freq=2462 MHz)
Sep 23 17:49:43 localhost kernel: [ 4366.057162] wlan0: authenticated
Sep 23 17:49:43 localhost NetworkManager[966]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 23 17:49:43 localhost kernel: [ 4366.087022] wlan0: associate with 00:09:5b:9c:69:5a (try 1)
Sep 23 17:49:43 localhost kernel: [ 4366.089688] wlan0: RX AssocResp from 00:09:5b:9c:69:5a (capab=0x431 status=0 aid=1)
Sep 23 17:49:43 localhost kernel: [ 4366.089693] wlan0: associated
Sep 23 17:49:43 localhost wpa_supplicant[1043]: Associated with 00:09:5b:9c:69:5a
Sep 23 17:49:43 localhost kernel: [ 4366.102115] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 23 17:49:43 localhost NetworkManager[966]: <info> (wlan0): supplicant interface state: associating -> associated
Sep 23 17:49:43 localhost NetworkManager[966]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Sep 23 17:49:44 localhost wpa_supplicant[1043]: WPA: Key negotiation completed with 00:09:5b:9c:69:5a [PTK=TKIP GTK=TKIP]
Sep 23 17:49:44 localhost wpa_supplicant[1043]: CTRL-EVENT-CONNECTED - Connection to 00:09:5b:9c:69:5a completed (auth) [id=0 id_str=]
Sep 23 17:49:44 localhost NetworkManager[966]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Sep 23 17:49:44 localhost NetworkManager[966]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'VIRUS'.
Sep 23 17:49:44 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 23 17:49:44 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 23 17:49:44 localhost NetworkManager[966]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 23 17:49:44 localhost NetworkManager[966]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 23 17:49:44 localhost dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Sep 23 17:49:44 localhost dhclient: Copyright 2004-2011 Internet Systems Consortium.
Sep 23 17:49:44 localhost dhclient: All rights reserved.
Sep 23 17:49:44 localhost dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 23 17:49:44 localhost dhclient: 
Sep 23 17:49:44 localhost NetworkManager[966]: <info> dhclient started with pid 28601
Sep 23 17:49:44 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 23 17:49:44 localhost NetworkManager[966]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 23 17:49:44 localhost dhclient: Listening on LPF/wlan0/00:1c:df:1c:7d:de
Sep 23 17:49:44 localhost dhclient: Sending on   LPF/wlan0/00:1c:df:1c:7d:de
Sep 23 17:49:44 localhost dhclient: Sending on   Socket/fallback
Sep 23 17:49:44 localhost dhclient: DHCPREQUEST of 192.168.0.60 on wlan0 to 255.255.255.255 port 67
Sep 23 17:49:44 localhost dhclient: DHCPACK of 192.168.0.60 from 192.168.0.10
Sep 23 17:49:44 localhost dhclient: bound to 192.168.0.60 -- renewal in 18742 seconds.
Sep 23 17:49:44 localhost NetworkManager[966]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Sep 23 17:49:44 localhost NetworkManager[966]: <info>   address 192.168.0.60
Sep 23 17:49:44 localhost NetworkManager[966]: <info>   prefix 24 (255.255.255.0)
Sep 23 17:49:44 localhost NetworkManager[966]: <info>   gateway 192.168.0.10
Sep 23 17:49:44 localhost NetworkManager[966]: <info>   hostname 'energico'
Sep 23 17:49:44 localhost NetworkManager[966]: <info>   nameserver '192.168.0.10'
Sep 23 17:49:44 localhost NetworkManager[966]: <info>   domain name 'tir-na-nog.sytes.net'
Sep 23 17:49:44 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 23 17:49:44 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep 23 17:49:45 localhost NetworkManager[966]: <info> DNS: starting dnsmasq...
Sep 23 17:49:45 localhost NetworkManager[966]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep 23 17:49:45 localhost dnsmasq[28604]: failed to create listening socket for 127.0.0.1: Address already in use
Sep 23 17:49:45 localhost dnsmasq[28604]: FAILED to start up
Sep 23 17:49:45 localhost NetworkManager[966]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep 23 17:49:45 localhost NetworkManager[966]: <info> Policy set 'VIRUS' (wlan0) as default for IPv4 routing and DNS.
Sep 23 17:49:45 localhost NetworkManager[966]: <info> Activation (wlan0) successful, device activated.
Sep 23 17:49:45 localhost NetworkManager[966]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 23 17:49:45 localhost dbus[927]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 23 17:49:45 localhost NetworkManager[966]: <warn> dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
Sep 23 17:49:45 localhost NetworkManager[966]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep 23 17:49:45 localhost dbus[927]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 23 17:49:45 localhost ntpdate[28708]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Sep 23 17:49:45 localhost ntpdate[28708]: no servers can be used, exiting
Sep 23 17:49:47 localhost dnsmasq[1328]: reading /var/run/dnsmasq/resolv.conf
Sep 23 17:49:47 localhost dnsmasq[1328]: using nameserver 192.168.0.10#53

```

Ant guidance would be appreciated,

thanks.

---

### Post by brazzmonkey on 2012-09-24
here is further info :
```
Bus 001 Device 007: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2571W]
```
```
$ lsmod
Module                  Size  Used by
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20061  1 rt73usb
rt2x00lib              48805  2 rt73usb,rt2x00usb
mac80211              436455  2 rt2x00usb,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
arc4                   12473  2 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
binfmt_misc            17292  1 
dm_crypt               22528  0 
snd_hda_codec_analog    75395  1 
ppdev                  12849  0 
dcdbas                 14098  0 
usblp                  17885  0 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
psmouse                72919  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  1 
snd                    62064  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
i915                  414817  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
tg3                   141369  0 
```

---

### Post by brazzmonkey on 2012-09-24
Here is what syslog gives upon disconnection :
```
Sep 24 10:04:11 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 24 10:04:13 localhost wpa_supplicant[2383]: Trying to authenticate with 00:09:5b:9c:69:5a (SSID='VIRUS' freq=2462 MHz)
Sep 24 10:04:13 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 24 10:04:13 localhost kernel: [ 2756.494564] wlan0: authenticate with 00:09:5b:9c:69:5a (try 1)
Sep 24 10:04:13 localhost wpa_supplicant[2383]: Trying to associate with 00:09:5b:9c:69:5a (SSID='VIRUS' freq=2462 MHz)
Sep 24 10:04:13 localhost kernel: [ 2756.496449] wlan0: authenticated
Sep 24 10:04:13 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 24 10:04:13 localhost kernel: [ 2756.516063] wlan0: associate with 00:09:5b:9c:69:5a (try 1)
Sep 24 10:04:13 localhost kernel: [ 2756.518816] wlan0: RX ReassocResp from 00:09:5b:9c:69:5a (capab=0x431 status=0 aid=1)
Sep 24 10:04:13 localhost kernel: [ 2756.518821] wlan0: associated
Sep 24 10:04:13 localhost wpa_supplicant[2383]: Associated with 00:09:5b:9c:69:5a
Sep 24 10:04:13 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: associating -> associated
Sep 24 10:04:16 localhost kernel: [ 2760.072198] wlan0: deauthenticated from 00:09:5b:9c:69:5a (Reason: 4)
Sep 24 10:04:16 localhost wpa_supplicant[2383]: CTRL-EVENT-DISCONNECTED bssid=00:09:5b:9c:69:5a reason=4
Sep 24 10:04:16 localhost kernel: [ 2760.093841] cfg80211: All devices are disconnected, going to restore regulatory settings
Sep 24 10:04:16 localhost kernel: [ 2760.093848] cfg80211: Restoring regulatory settings
Sep 24 10:04:16 localhost kernel: [ 2760.093855] cfg80211: Calling CRDA to update world regulatory domain
Sep 24 10:04:16 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: associated -> disconnected
Sep 24 10:04:16 localhost kernel: [ 2760.101653] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101661] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101666] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101672] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101677] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101683] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101687] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101693] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101698] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101703] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101708] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101713] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101718] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101723] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101728] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101734] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101739] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101744] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101749] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101754] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101759] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101765] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101769] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101775] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101780] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101785] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101790] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:16 localhost kernel: [ 2760.101796] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101801] cfg80211: World regulatory domain updated:
Sep 24 10:04:16 localhost kernel: [ 2760.101805] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 24 10:04:16 localhost kernel: [ 2760.101811] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101816] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101821] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101826] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost kernel: [ 2760.101831] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:16 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 24 10:04:18 localhost wpa_supplicant[2383]: Trying to authenticate with 00:09:5b:9c:69:5a (SSID='VIRUS' freq=2462 MHz)
Sep 24 10:04:18 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 24 10:04:18 localhost kernel: [ 2761.482441] wlan0: authenticate with 00:09:5b:9c:69:5a (try 1)
Sep 24 10:04:18 localhost wpa_supplicant[2383]: Trying to associate with 00:09:5b:9c:69:5a (SSID='VIRUS' freq=2462 MHz)
Sep 24 10:04:18 localhost kernel: [ 2761.484201] wlan0: authenticated
Sep 24 10:04:18 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 24 10:04:18 localhost kernel: [ 2761.503813] wlan0: associate with 00:09:5b:9c:69:5a (try 1)
Sep 24 10:04:18 localhost kernel: [ 2761.506449] wlan0: RX ReassocResp from 00:09:5b:9c:69:5a (capab=0x431 status=0 aid=1)
Sep 24 10:04:18 localhost kernel: [ 2761.506454] wlan0: associated
Sep 24 10:04:18 localhost wpa_supplicant[2383]: Associated with 00:09:5b:9c:69:5a
Sep 24 10:04:18 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: associating -> associated
Sep 24 10:04:21 localhost kernel: [ 2765.059576] wlan0: deauthenticated from 00:09:5b:9c:69:5a (Reason: 4)
Sep 24 10:04:21 localhost wpa_supplicant[2383]: CTRL-EVENT-DISCONNECTED bssid=00:09:5b:9c:69:5a reason=4
Sep 24 10:04:21 localhost kernel: [ 2765.081843] cfg80211: All devices are disconnected, going to restore regulatory settings
Sep 24 10:04:21 localhost kernel: [ 2765.081851] cfg80211: Restoring regulatory settings
Sep 24 10:04:21 localhost kernel: [ 2765.081858] cfg80211: Calling CRDA to update world regulatory domain
Sep 24 10:04:21 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: associated -> disconnected
Sep 24 10:04:21 localhost kernel: [ 2765.089276] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089282] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089285] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089288] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089291] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089295] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089297] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089301] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089303] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089307] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089309] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089313] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089316] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089319] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089322] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089325] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089328] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089331] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089334] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089338] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089340] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089344] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089347] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089350] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089353] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089356] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089359] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:21 localhost kernel: [ 2765.089362] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089366] cfg80211: World regulatory domain updated:
Sep 24 10:04:21 localhost kernel: [ 2765.089368] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 24 10:04:21 localhost kernel: [ 2765.089371] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089374] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089377] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089380] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost kernel: [ 2765.089384] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:21 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 24 10:04:23 localhost wpa_supplicant[2383]: Trying to authenticate with 00:09:5b:9c:69:5a (SSID='VIRUS' freq=2462 MHz)
Sep 24 10:04:23 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 24 10:04:23 localhost kernel: [ 2766.470816] wlan0: authenticate with 00:09:5b:9c:69:5a (try 1)
Sep 24 10:04:23 localhost wpa_supplicant[2383]: Trying to associate with 00:09:5b:9c:69:5a (SSID='VIRUS' freq=2462 MHz)
Sep 24 10:04:23 localhost kernel: [ 2766.472702] wlan0: authenticated
Sep 24 10:04:23 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 24 10:04:23 localhost kernel: [ 2766.492192] wlan0: associate with 00:09:5b:9c:69:5a (try 1)
Sep 24 10:04:23 localhost kernel: [ 2766.494822] wlan0: RX ReassocResp from 00:09:5b:9c:69:5a (capab=0x431 status=0 aid=1)
Sep 24 10:04:23 localhost kernel: [ 2766.494827] wlan0: associated
Sep 24 10:04:23 localhost wpa_supplicant[2383]: Associated with 00:09:5b:9c:69:5a
Sep 24 10:04:23 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: associating -> associated
Sep 24 10:04:23 localhost NetworkManager[936]: <warn> Activation (wlan0/wireless): association took too long.
Sep 24 10:04:23 localhost NetworkManager[936]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 24 10:04:23 localhost NetworkManager[936]: <warn> Activation (wlan0/wireless): asking for new secrets
Sep 24 10:04:23 localhost kernel: [ 2767.018184] wlan0: deauthenticating from 00:09:5b:9c:69:5a by local choice (reason=3)
Sep 24 10:04:23 localhost wpa_supplicant[2383]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Sep 24 10:04:23 localhost NetworkManager[936]: <info> (wlan0): supplicant interface state: associated -> disconnected
Sep 24 10:04:23 localhost NetworkManager[936]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Sep 24 10:04:23 localhost kernel: [ 2767.053821] cfg80211: All devices are disconnected, going to restore regulatory settings
Sep 24 10:04:23 localhost kernel: [ 2767.053830] cfg80211: Restoring regulatory settings
Sep 24 10:04:23 localhost kernel: [ 2767.053863] cfg80211: Calling CRDA to update world regulatory domain
Sep 24 10:04:23 localhost kernel: [ 2767.062059] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062065] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062070] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062074] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062078] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062082] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062085] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062090] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062093] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062097] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062101] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062105] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062108] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062112] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062116] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062120] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062124] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062128] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062131] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062135] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062139] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062143] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062147] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062151] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062154] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062158] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062162] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Sep 24 10:04:23 localhost kernel: [ 2767.062166] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062170] cfg80211: World regulatory domain updated:
Sep 24 10:04:23 localhost kernel: [ 2767.062173] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 24 10:04:23 localhost kernel: [ 2767.062177] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062181] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062185] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062189] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:23 localhost kernel: [ 2767.062193] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 24 10:04:27 localhost NetworkManager[936]: <warn> No agents were available for this request.
Sep 24 10:04:27 localhost NetworkManager[936]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Sep 24 10:04:27 localhost NetworkManager[936]: <warn> Activation (wlan0) failed for access point (VIRUS)
Sep 24 10:04:27 localhost NetworkManager[936]: <info> Marking connection 'VIRUS' invalid.
Sep 24 10:04:27 localhost NetworkManager[936]: <warn> Activation (wlan0) failed.
Sep 24 10:04:27 localhost NetworkManager[936]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep 24 10:04:27 localhost NetworkManager[936]: <info> (wlan0): deactivating device (reason 'none') [0]
```

---

### Post by brazzmonkey on 2012-09-24
As a workaround I dropped networkmanager for wicd, which seems more robust. At least it's able to reconnect automatically.

---

