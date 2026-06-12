---
title: "Thinkpad x220 only associates on 5 Ghz channels"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by ttosttos on 2013-05-11
Since upgrading to 12.04, I've had recurring problems with one of the wireless networks I regularly connect to.  First, it was a WPA-Enterprise bug ([https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343)). After that fix, I'm able to connect  occasionally.  When reviewing logs, it seems that association fails every time it is attempted on a 2 GHz channel.  Every successful connection seems to be on 5 GHz channels.  This is a large wireless network with thousands of wireless endpoints and Cisco access points.   Here are the logs for one of failed and and success connection:

May  8 09:18:29 ohlone NetworkManager[1019]: <info> Auto-activating connection 'xxxxxxxx'.
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) starting connection 'xxxxxxxx'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  8 09:18:29 ohlone NetworkManager[1019]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0/wireless): access point 'xxxxxxxx' has security, but secrets are required.
May  8 09:18:29 ohlone NetworkManager[1019]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  8 09:18:29 ohlone NetworkManager[1019]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  8 09:18:29 ohlone NetworkManager[1019]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0/wireless): connection 'xxxxxxxx' has security, and secrets exist.  No new secrets needed.
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'ssid' value 'xxxxxxxx'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'scan_ssid' value '1'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'key_mgmt' value 'WPA-EAP'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'auth_alg' value 'OPEN'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'password' value '<omitted>'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'eap' value 'PEAP'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'fragment_size' value '1300'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'identity' value 'xxxxx\xxxxxxxx'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: added 'bgscan' value 'simple:30:-45:300'
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  8 09:18:29 ohlone NetworkManager[1019]: <info> Config: set interface ap_scan to 1
May  8 09:18:29 ohlone NetworkManager[1019]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May  8 09:18:31 ohlone wpa_supplicant[1813]: Trying to authenticate with 6c:9c:ed:ec:9b:80 (SSID='xxxxxxxx' freq=2462 MHz)
May  8 09:18:31 ohlone NetworkManager[1019]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May  8 09:18:31 ohlone kernel: [87987.182359] wlan0: direct probe to 6c:9c:ed:ec:9b:80 (try 1/3)
May  8 09:18:31 ohlone kernel: [87987.380300] wlan0: direct probe to 6c:9c:ed:ec:9b:80 (try 2/3)
May  8 09:18:32 ohlone kernel: [87987.579854] wlan0: direct probe to 6c:9c:ed:ec:9b:80 (try 3/3)
May  8 09:18:32 ohlone kernel: [87987.779430] wlan0: direct probe to 6c:9c:ed:ec:9b:80 timed out
May  8 09:18:39 ohlone wpa_supplicant[1813]: Trying to authenticate with 6c:9c:ed:ec:92:9f (SSID='xxxxxxxx' freq=5220 MHz)
May  8 09:18:39 ohlone wpa_supplicant[1813]: Trying to associate with 6c:9c:ed:ec:92:9f (SSID='xxxxxxxx' freq=5220 MHz)
May  8 09:18:39 ohlone kernel: [87994.941289] wlan0: authenticate with 6c:9c:ed:ec:92:9f (try 1)
May  8 09:18:39 ohlone kernel: [87994.942001] wlan0: authenticated
May  8 09:18:39 ohlone NetworkManager[1019]: <info> (wlan0): supplicant interface state: authenticating -> associating
May  8 09:18:39 ohlone kernel: [87994.956664] wlan0: associate with 6c:9c:ed:ec:92:9f (try 1)
May  8 09:18:39 ohlone kernel: [87995.154702] wlan0: associate with 6c:9c:ed:ec:92:9f (try 2)
May  8 09:18:39 ohlone kernel: [87995.156525] wlan0: RX AssocResp from 6c:9c:ed:ec:92:9f (capab=0x11 status=0 aid=8)
May  8 09:18:39 ohlone kernel: [87995.156535] wlan0: associated
May  8 09:18:39 ohlone wpa_supplicant[1813]: Associated with 6c:9c:ed:ec:92:9f
May  8 09:18:39 ohlone wpa_supplicant[1813]: CTRL-EVENT-EAP-STARTED EAP authentication started
May  8 09:18:39 ohlone kernel: [87995.166133] cfg80211: Calling CRDA for country: US
May  8 09:18:39 ohlone wpa_supplicant[1813]: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
May  8 09:18:39 ohlone wpa_supplicant[1813]: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
May  8 09:18:39 ohlone NetworkManager[1019]: <info> (wlan0): supplicant interface state: associating -> associated
May  8 09:18:39 ohlone kernel: [87995.173208] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173212] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173214] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173216] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173218] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173221] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173223] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173225] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173227] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173229] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173231] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173233] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173235] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173236] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173238] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173240] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173242] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173244] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173246] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173248] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173250] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173252] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173254] cfg80211: Disabling freq 2467 MHz
May  8 09:18:39 ohlone kernel: [87995.173255] cfg80211: Disabling freq 2472 MHz
May  8 09:18:39 ohlone kernel: [87995.173257] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173259] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173261] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173263] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173264] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173266] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173268] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173271] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173273] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173274] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173276] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173277] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173279] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173280] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173282] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173283] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173285] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173286] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173301] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173310] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173321] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173324] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173326] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173328] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173329] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173332] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173333] cfg80211: Disabling freq 5600 MHz
May  8 09:18:39 ohlone kernel: [87995.173335] cfg80211: Disabling freq 5620 MHz
May  8 09:18:39 ohlone kernel: [87995.173336] cfg80211: Disabling freq 5640 MHz
May  8 09:18:39 ohlone kernel: [87995.173337] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173339] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173341] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173343] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173345] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173348] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173350] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173352] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173354] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173356] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173357] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173359] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173360] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173362] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173364] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
May  8 09:18:39 ohlone kernel: [87995.173366] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173371] cfg80211: Regulatory domain changed to country: US
May  8 09:18:39 ohlone kernel: [87995.173372] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May  8 09:18:39 ohlone kernel: [87995.173375] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173376] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
May  8 09:18:39 ohlone kernel: [87995.173378] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173380] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173381] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 09:18:39 ohlone kernel: [87995.173383] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May  8 09:18:39 ohlone wpa_supplicant[1813]: CTRL-EVENT-EAP-PEER-CERT depth=2 subject='/O=Digital Signature Trust Co./CN=DST Root CA X3'
May  8 09:18:39 ohlone wpa_supplicant[1813]: CTRL-EVENT-EAP-PEER-CERT depth=2 subject='/O=Digital Signature Trust Co./CN=DST Root CA X3'
May  8 09:18:39 ohlone wpa_supplicant[1813]: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/O=xxxxx xxxxxxx/CN=xxxxx SSCA2'
May  8 09:18:39 ohlone wpa_supplicant[1813]: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='/CN=xx-xxx-xx-x-x.xxxxx.com'
May  8 09:18:39 ohlone kernel: [87995.232153] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
May  8 09:18:39 ohlone wpa_supplicant[1813]: EAP-MSCHAPV2: Authentication succeeded
May  8 09:18:39 ohlone wpa_supplicant[1813]: CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
May  8 09:18:39 ohlone wpa_supplicant[1813]: WPA: Key negotiation completed with 6c:9c:ed:ec:92:9f [PTK=CCMP GTK=CCMP]
May  8 09:18:39 ohlone wpa_supplicant[1813]: CTRL-EVENT-CONNECTED - Connection to 6c:9c:ed:ec:92:9f completed (auth) [id=0 id_str=]
May  8 09:18:39 ohlone NetworkManager[1019]: <info> (wlan0): supplicant interface state: associated -> completed
May  8 09:18:39 ohlone NetworkManager[1019]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'xxxxxxxx'.

Here are some additional details

xx@ohlone:~$ lspci -vv
<snip>
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 46
    Region 0: Memory at f2400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

<snip>
xx@ohlone:~$ lsmod | grep iwlwifi
iwlwifi               401140  0 
mac80211              506862  1 iwlwifi
cfg80211              205774  2 iwlwifi,mac80211
xx@ohlone:~$ 

xx@ohlone:~$ sudo lshw -C network
<snip>
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 8c:70:5a:24:76:dc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-38-generic firmware=18.168.6.1 ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f2400000-f2401fff
xx@ohlone:~$ 
xx@ohlone:~$ uname -mr
3.2.0-38-generic x86_64
saalvare@ohlone:~$ 






I connect fine on 2 Ghz channels to another 802.11n network with a D-Link access point.

Any ideas/suggestions?  Should I give ndiswrapper a try?

---

