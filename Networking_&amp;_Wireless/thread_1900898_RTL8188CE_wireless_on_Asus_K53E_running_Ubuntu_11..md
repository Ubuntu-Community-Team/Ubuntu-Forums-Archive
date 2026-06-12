---
title: "RTL8188CE wireless on Asus K53E running Ubuntu 11.10"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by Flash__Gordon on 2011-12-27
Hi, I have just within the last week received a new Asus laptop (A53E with K53E MOBO) with a RTL8188CE PCI-E wireless. It is using the kernal driver but I am having internet issues of slow downs where if I shut off wireless (at laptop) and then turn on and allow to reconnect it will be fine for a time. I have several laptops here and am only having this issue with the ones using this or a variant of this chipset so have narrowed it down to this. When it happens I can't even get into the router but can from one of the other laptops running a B43 chipset. Here is info for you. 

david@david-asus:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: AzureWave Device [1a3b:1139]
	Kernel driver in use: rtl8192ce
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c

david@david-asus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Gordon"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:21:29:B2:F1:57   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0



david@david-asus:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 USB Controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
david@david-asus:~$ 



I noticed there is an update driver on the realtek web site (nov 22). Will installing this driver replace the kernel driver or do I have to uninstall that first? If so how. 
my router is Linksys WRT54G2 / GS2 maybe an 'n' issue?
Thanks in advance.

---

### Post by Flash__Gordon on 2011-12-27
no thoughts? Will kernel driver automatically be replaced if I install drivers from Realtek?

---

### Post by Flash__Gordon on 2011-12-28
no gurus out there can offer advice? Even a yes or no for acknowledgement would be great!

Flash

---

### Post by nailuii on 2011-12-31
I have the same card here, however in a Thinkpad E-125 (AMD E-450). I tried the kernel version and the updated version on the realtek site same thing: after a while the wireless disconnects. The router is a TP-Link WR841N with all security disabled (no WEP, WPA everything off). The router is fine, it works with my other devices. Signal strength is good, I'm in the same room with the router and there are only two other neighboring networks around (both with weak signals)

I get these in syslog: 
```

Jan  1 00:08:25 the-edge wpa_supplicant[1065]: Trying to authenticate with 54:e6:fc:a0:4a:74 (SSID='tplink' freq=2462 MHz)
Jan  1 00:08:25 the-edge kernel: [30701.651261] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 1/3)
Jan  1 00:08:25 the-edge kernel: [30701.848138] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 2/3)
Jan  1 00:08:26 the-edge kernel: [30702.048414] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 3/3)
Jan  1 00:08:26 the-edge kernel: [30702.248482] wlan0: direct probe to 54:e6:fc:a0:4a:74 timed out
Jan  1 00:08:37 the-edge wpa_supplicant[1065]: Trying to authenticate with 54:e6:fc:a0:4a:74 (SSID='tplink' freq=2462 MHz)
Jan  1 00:08:37 the-edge kernel: [30714.012292] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 1/3)
Jan  1 00:08:38 the-edge kernel: [30714.212166] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 2/3)
Jan  1 00:08:38 the-edge kernel: [30714.412212] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 3/3)
Jan  1 00:08:38 the-edge kernel: [30714.612153] wlan0: direct probe to 54:e6:fc:a0:4a:74 timed out
Jan  1 00:08:44 the-edge wpa_supplicant[1065]: Trying to authenticate with 54:e6:fc:a0:4a:74 (SSID='tplink' freq=2462 MHz)
Jan  1 00:08:44 the-edge kernel: [30720.491082] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 1/3)
Jan  1 00:08:44 the-edge kernel: [30720.688117] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 2/3)
Jan  1 00:08:44 the-edge kernel: [30720.888175] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 3/3)
Jan  1 00:08:45 the-edge kernel: [30721.088119] wlan0: direct probe to 54:e6:fc:a0:4a:74 timed out

```then some of these:
```

Jan  1 00:11:55 the-edge wpa_supplicant[1065]: Trying to authenticate with 54:e6:fc:a0:4a:74 (SSID='tplink' freq=2462 MHz)
Jan  1 00:11:55 the-edge kernel: [30912.012167] wlan0: direct probe to 54:e6:fc:a0:4a:74 (try 1/3)
Jan  1 00:11:56 the-edge kernel: [30912.086437] wlan0: direct probe responded
Jan  1 00:11:56 the-edge kernel: [30912.092307] wlan0: authenticate with 54:e6:fc:a0:4a:74 (try 1)
Jan  1 00:11:56 the-edge kernel: [30912.292245] wlan0: authenticate with 54:e6:fc:a0:4a:74 (try 2)
Jan  1 00:11:56 the-edge kernel: [30912.496193] wlan0: authenticate with 54:e6:fc:a0:4a:74 (try 3)
Jan  1 00:11:56 the-edge kernel: [30912.696317] wlan0: authentication with 54:e6:fc:a0:4a:74 timed out
Jan  1 00:12:02 the-edge wpa_supplicant[1065]: Trying to authenticate with 54:e6:fc:a0:4a:74 (SSID='tplink' freq=2462 MHz)
Jan  1 00:12:02 the-edge kernel: [30918.595244] wlan0: authenticate with 54:e6:fc:a0:4a:74 (try 1)
Jan  1 00:12:02 the-edge kernel: [30918.792105] wlan0: authenticate with 54:e6:fc:a0:4a:74 (try 2)
Jan  1 00:12:02 the-edge kernel: [30918.992440] wlan0: authenticate with 54:e6:fc:a0:4a:74 (try 3)
Jan  1 00:12:03 the-edge kernel: [30919.192205] wlan0: authentication with 54:e6:fc:a0:4a:74 timed out

```When I finally do get connected after a while I get this:

```

Jan  1 00:31:43 the-edge wpa_supplicant[1065]: CTRL-EVENT-DISCONNECTED bssid=54:e6:fc:a0:4a:74 reason=4
Jan  1 00:31:43 the-edge kernel: [32099.465163] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan  1 00:31:43 the-edge kernel: [32099.465179] cfg80211: Restoring regulatory settings
Jan  1 00:31:43 the-edge kernel: [32099.465192] cfg80211: Calling CRDA to update world regulatory domain
Jan  1 00:31:43 the-edge kernel: [32099.477465] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jan  1 00:31:43 the-edge kernel: [32099.477482] cfg80211: World regulatory domain updated:
Jan  1 00:31:43 the-edge kernel: [32099.477488] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  1 00:31:43 the-edge kernel: [32099.477518] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  1 00:31:43 the-edge kernel: [32099.477528] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  1 00:31:43 the-edge kernel: [32099.477537] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  1 00:31:43 the-edge kernel: [32099.477546] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  1 00:31:43 the-edge kernel: [32099.477554] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  1 00:31:43 the-edge NetworkManager[845]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jan  1 00:31:43 the-edge NetworkManager[845]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  1 00:31:44 the-edge NetworkManager[845]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  1 00:31:46 the-edge NetworkManager[845]: <info> (wlan0): roamed from BSSID 54:E6:FC:A0:4A:74 (tplink) to (none) ((none))
Jan  1 00:31:58 the-edge NetworkManager[845]: <warn> (wlan0): link timed out.
Jan  1 00:31:58 the-edge NetworkManager[845]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Jan  1 00:31:58 the-edge NetworkManager[845]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 13764
Jan  1 00:31:59 the-edge avahi-daemon[847]: Withdrawing address record for 192.168.1.100 on wlan0.
Jan  1 00:31:59 the-edge avahi-daemon[847]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Jan  1 00:31:59 the-edge avahi-daemon[847]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Auto-activating connection 'tplink'.
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Activation (wlan0) starting connection 'tplink'
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Activation (wlan0/wireless): connection 'tplink' requires no security.  No secrets needed.
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Config: added 'ssid' value 'tplink'
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Config: added 'scan_ssid' value '1'
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Config: added 'key_mgmt' value 'NONE'
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  1 00:31:59 the-edge dbus[821]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  1 00:31:59 the-edge NetworkManager[845]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jan  1 00:31:59 the-edge NetworkManager[845]: <info> Config: set interface ap_scan to 1
Jan  1 00:31:59 the-edge dbus[821]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  1 00:32:02 the-edge NetworkManager[845]: <info> (wlan0): supplicant interface state: disconnected -> scanning

```Then it sometimes connects, sometimes direct probe timeouts, sometimes authentication timeouts. Note that in all this time, I have not moved and there is no other wireless router named tplink around (so no roaming).

---

### Post by nailuii on 2012-01-02
Well it seems I can work-around my connection issues by configuring the router with Channel: Auto (previously I had set it to work only on a specific radio channel) - note that this is with the latest 11.10 kernel and the driver from the Realtek website.

---

### Post by Flash__Gordon on 2012-01-02
> **nailuii said:**
> Well it seems I can work-around my connection issues by configuring the router with Channel: Auto (previously I had set it to work only on a specific radio channel) - note that this is with the latest 11.10 kernel and the driver from the Realtek website.

 Interesting, I will try this.

Flash

---

