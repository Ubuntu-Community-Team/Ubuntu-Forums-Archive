---
title: "Intel Ultimate N 6300 in Thinkpad X230, drop-outs and no connection"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by Earsplit on 2012-09-10
Hey all,

Just picked up a Lenovo X230. Everything has been working FLAWLESSLY, except the wifi. Here at school, we use PEAP with WPA2-enterprise. I have serious difficulty connecting to the network.

My wireless card is an Intel Ultimate-N 6300 with 3 antennas.

I tried playing with the following modprobe modules:
11n_disable, power_save, swcrypto, bt_coex_active
Without wireless N, I got dropouts less frequently but they still happened. The other two parameters I used with wireless N, but they didn't solve much.


```


 > uname -r

3.2.0-30-generic

 > dmesg | grep iwl

[ 4505.650327] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 4505.657069] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[ 8992.468190] iwlwifi 0000:03:00.0: PCI INT A disabled
[ 9256.148984] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 9256.149051] iwlwifi 0000:03:00.0: setting latency timer to 64
[ 9256.149092] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[ 9256.149093] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900050b4000
[ 9256.149095] iwlwifi 0000:03:00.0: HW Revision ID = 0x3E
[ 9256.149394] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[ 9256.149503] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[ 9256.149689] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 9256.167372] iwlwifi 0000:03:00.0: device EEPROM VER=0x43a, CALIB=0x6
[ 9256.167374] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[ 9256.167375] iwlwifi 0000:03:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[ 9256.167390] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 9256.174596] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[ 9256.175654] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 9398.048710] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 9398.055484] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[ 9398.302922] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 9398.309655] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1

 > lspci

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 07)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)

 > iwconfig

wlan0     IEEE 802.11abgn  ESSID:"school.edu"  
          Mode:Managed  Frequency:5.765 GHz  Access Point: D8:C7:C8:A1:C8:E8   
          Bit Rate=81 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by Earsplit on 2012-09-11
Anybody?

I'm about to update the kernel, since this seems to be a driver issue that has been fixed for some.

Anything I should know before updating the kernel?

---

### Post by rfporto on 2012-09-12
I have the same laptop and configuration, with the newest kernel for 12.04 and I am having the same problem.  I too have disabled power management as well as wireless n, but the problem still persists.  Everything works fantastically on my home router, the only times I have issues are when I am on my college's wifi.

---

### Post by Earsplit on 2012-09-12
^Thanks for the support. I love how Ubuntu runs on this laptop, but I can't keep using it at school if I can't get wifi =[[[[

Relevant info from the syslog on an UNENCRYPTED network (guest network at school)
```

 > sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n80

Sep 12 13:15:54 x230 avahi-daemon[923]: New relevant interface wlan0.IPv6 for mDNS.
Sep 12 13:15:54 x230 avahi-daemon[923]: Registering new address record for fe80::2677:3ff:fe73:a14 on wlan0.*.
Sep 12 13:16:03 x230 kernel: [ 3148.209099] wlan0: no IPv6 routers present
Sep 12 13:16:13 x230 NetworkManager[912]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 12 13:16:13 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 12 13:16:13 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 12 13:16:13 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 12 13:16:30 x230 wpa_supplicant[1010]: Trying to authenticate with d8:c7:c8:a1:c1:e1 (SSID='bucknell_guests' freq=2412 MHz)
Sep 12 13:16:30 x230 kernel: [ 3174.749757] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 1/3)
Sep 12 13:16:30 x230 kernel: [ 3174.947695] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 2/3)
Sep 12 13:16:30 x230 kernel: [ 3175.147401] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 3/3)
Sep 12 13:16:30 x230 NetworkManager[912]: <info> Policy set 'bucknell_guests' (wlan0) as default for IPv4 routing and DNS.
Sep 12 13:16:30 x230 NetworkManager[912]: <info> Policy set 'bucknell_guests' (wlan0) as default for IPv4 routing and DNS.
Sep 12 13:16:30 x230 kernel: [ 3175.347152] wlan0: direct probe to d8:c7:c8:a1:c1:e1 timed out
Sep 12 13:16:30 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 12 13:16:35 x230 kernel: [ 3179.842354] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:a1:c8:e9 tid = 0
Sep 12 13:16:42 x230 kernel: [ 3186.871750] wlan0: deauthenticating from d8:c7:c8:a1:c8:e9 by local choice (reason=2)
Sep 12 13:16:42 x230 wpa_supplicant[1010]: Trying to authenticate with d8:c7:c8:a1:c8:e1 (SSID='bucknell_guests' freq=2462 MHz)
Sep 12 13:16:42 x230 wpa_supplicant[1010]: CTRL-EVENT-DISCONNECTED bssid=d8:c7:c8:a1:c8:e1 reason=2
Sep 12 13:16:42 x230 kernel: [ 3186.984669] wlan0: direct probe to d8:c7:c8:a1:c8:e1 (try 1/3)
Sep 12 13:16:42 x230 kernel: [ 3187.183867] wlan0: direct probe to d8:c7:c8:a1:c8:e1 (try 2/3)
Sep 12 13:16:42 x230 kernel: [ 3187.383605] wlan0: direct probe to d8:c7:c8:a1:c8:e1 (try 3/3)
Sep 12 13:16:42 x230 kernel: [ 3187.583348] wlan0: direct probe to d8:c7:c8:a1:c8:e1 timed out
Sep 12 13:16:44 x230 NetworkManager[912]: <info> (wlan0): roamed from BSSID D8:C7:C8:A1:C8:E9 (bucknell_guests) to (none) ((none))
Sep 12 13:16:46 x230 dhclient: Listening on LPF/wlan0/24:77:03:73:0a:14
Sep 12 13:16:46 x230 dhclient: Sending on   LPF/wlan0/24:77:03:73:0a:14
Sep 12 13:16:46 x230 dhclient: DHCPRELEASE on wlan0 to 172.20.2.2 port 67
Sep 12 13:16:46 x230 avahi-daemon[923]: Withdrawing address record for 10.101.21.91 on wlan0.
Sep 12 13:16:46 x230 avahi-daemon[923]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.101.21.91.
Sep 12 13:16:46 x230 avahi-daemon[923]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep 12 13:16:46 x230 avahi-daemon[923]: Interface wlan0.IPv6 no longer relevant for mDNS.
Sep 12 13:16:46 x230 avahi-daemon[923]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::2677:3ff:fe73:a14.
Sep 12 13:16:46 x230 avahi-daemon[923]: Withdrawing address record for fe80::2677:3ff:fe73:a14 on wlan0.
Sep 12 13:16:46 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 12 13:16:46 x230 kernel: [ 3191.300847] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
Sep 12 13:16:46 x230 kernel: [ 3191.307614] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
Sep 12 13:16:46 x230 kernel: [ 3191.515847] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 12 13:16:47 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 12 13:16:47 x230 NetworkManager[912]: <info> wpa_supplicant stopped
Sep 12 13:16:47 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: authenticating -> down
Sep 12 13:16:47 x230 NetworkManager[912]: <info> (wlan0): device state change: activated -> unavailable (reason 'supplicant-failed') [100 20 10]
Sep 12 13:16:47 x230 dbus[863]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Sep 12 13:16:47 x230 dbus[863]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Sep 12 13:16:47 x230 NetworkManager[912]: <info> (wlan0): deactivating device (reason 'supplicant-failed') [10]
Sep 12 13:16:47 x230 NetworkManager[912]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 6527
Sep 12 13:16:47 x230 NetworkManager[912]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep 12 13:16:47 x230 kernel: [ 3192.146485] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 12 13:16:47 x230 NetworkManager[912]: <info> wpa_supplicant started
Sep 12 13:16:47 x230 kernel: [ 3192.358423] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
Sep 12 13:16:47 x230 kernel: [ 3192.365225] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
Sep 12 13:16:47 x230 kernel: [ 3192.553996] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 12 13:16:47 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: starting -> ready
Sep 12 13:16:47 x230 NetworkManager[912]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Sep 12 13:16:47 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: ready -> inactive
Sep 12 13:16:52 x230 NetworkManager[912]: <info> Activation (wlan0) starting connection 'bucknell_guests'
Sep 12 13:16:52 x230 NetworkManager[912]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 12 13:16:52 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 12 13:16:52 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 12 13:16:52 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 12 13:16:52 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 12 13:16:52 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 12 13:16:52 x230 NetworkManager[912]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 12 13:16:52 x230 NetworkManager[912]: <info> Activation (wlan0/wireless): connection 'bucknell_guests' requires no security.  No secrets needed.
Sep 12 13:16:52 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 12 13:16:52 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: inactive -> scanning
Sep 12 13:16:55 x230 wpa_supplicant[6914]: Trying to authenticate with d8:c7:c8:a1:c1:e1 (SSID='bucknell_guests' freq=2412 MHz)
Sep 12 13:16:55 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 12 13:16:55 x230 kernel: [ 3200.084643] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 1/3)
Sep 12 13:16:55 x230 kernel: [ 3200.282884] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 2/3)
Sep 12 13:16:55 x230 kernel: [ 3200.482613] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 3/3)
Sep 12 13:16:56 x230 kernel: [ 3200.682351] wlan0: direct probe to d8:c7:c8:a1:c1:e1 timed out
Sep 12 13:16:57 x230 NetworkManager[912]: <info> wpa_supplicant die count reset
Sep 12 13:17:04 x230 wpa_supplicant[6914]: Trying to authenticate with d8:c7:c8:a1:c1:e1 (SSID='bucknell_guests' freq=2412 MHz)
Sep 12 13:17:04 x230 kernel: [ 3208.985957] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 1/3)
Sep 12 13:17:04 x230 kernel: [ 3209.183348] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 2/3)
Sep 12 13:17:04 x230 kernel: [ 3209.383079] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 3/3)
Sep 12 13:17:04 x230 kernel: [ 3209.582844] wlan0: direct probe to d8:c7:c8:a1:c1:e1 timed out

```

Syslog on an ENCRYPTED network
```


Sep 12 13:22:57 x230 NetworkManager[912]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 12 13:22:57 x230 NetworkManager[912]: <info> Activation (wlan0/wireless): connection 'bucknell.edu' has security, and secrets exist.  No new secrets needed.
Sep 12 13:22:57 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 12 13:22:57 x230 wpa_supplicant[6914]: Failed to initiate AP scan.
Sep 12 13:22:58 x230 wpa_supplicant[6914]: Failed to initiate AP scan.
Sep 12 13:22:59 x230 wpa_supplicant[6914]: Trying to authenticate with d8:c7:c8:a1:c1:e0 (SSID='bucknell.edu' freq=2412 MHz)
Sep 12 13:22:59 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Sep 12 13:22:59 x230 kernel: [ 3563.457141] wlan0: direct probe to d8:c7:c8:a1:c1:e0 (try 1/3)
Sep 12 13:22:59 x230 kernel: [ 3563.653457] wlan0: direct probe to d8:c7:c8:a1:c1:e0 (try 2/3)
Sep 12 13:22:59 x230 kernel: [ 3563.853154] wlan0: direct probe to d8:c7:c8:a1:c1:e0 (try 3/3)
Sep 12 13:22:59 x230 kernel: [ 3564.052986] wlan0: direct probe to d8:c7:c8:a1:c1:e0 timed out
Sep 12 13:23:08 x230 wpa_supplicant[6914]: Trying to authenticate with d8:c7:c8:a1:c1:e0 (SSID='bucknell.edu' freq=2412 MHz)
Sep 12 13:23:08 x230 kernel: [ 3572.253200] wlan0: direct probe to d8:c7:c8:a1:c1:e0 (try 1/3)
Sep 12 13:23:08 x230 kernel: [ 3572.450107] wlan0: direct probe to d8:c7:c8:a1:c1:e0 (try 2/3)
Sep 12 13:23:08 x230 kernel: [ 3572.649811] wlan0: direct probe to d8:c7:c8:a1:c1:e0 (try 3/3)
Sep 12 13:23:08 x230 kernel: [ 3572.849556] wlan0: direct probe to d8:c7:c8:a1:c1:e0 timed out
Sep 12 13:23:16 x230 wpa_supplicant[6914]: Trying to authenticate with d8:c7:c8:a1:c8:e0 (SSID='bucknell.edu' freq=2462 MHz)
Sep 12 13:23:16 x230 kernel: [ 3580.949248] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 1/3)
Sep 12 13:23:17 x230 kernel: [ 3581.146782] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 2/3)
Sep 12 13:23:17 x230 kernel: [ 3581.346500] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 3/3)
Sep 12 13:23:17 x230 kernel: [ 3581.546260] wlan0: direct probe to d8:c7:c8:a1:c8:e0 timed out
Sep 12 13:23:25 x230 wpa_supplicant[6914]: Trying to authenticate with d8:c7:c8:a1:c8:e0 (SSID='bucknell.edu' freq=2462 MHz)
Sep 12 13:23:25 x230 kernel: [ 3589.641547] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 1/3)
Sep 12 13:23:25 x230 kernel: [ 3589.839539] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 2/3)
Sep 12 13:23:25 x230 kernel: [ 3590.039279] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 3/3)
Sep 12 13:23:26 x230 kernel: [ 3590.239060] wlan0: direct probe to d8:c7:c8:a1:c8:e0 timed out
Sep 12 13:23:34 x230 wpa_supplicant[6914]: Trying to authenticate with d8:c7:c8:a1:c1:e0 (SSID='bucknell.edu' freq=2412 MHz)
Sep 12 13:23:34 x230 kernel: [ 3598.332491] wlan0: direct probe to d8:c7:c8:a1:c1:e0 (try 1/3)
Sep 12 13:23:34 x230 kernel: [ 3598.532297] wlan0: direct probe to d8:c7:c8:a1:c1:e0 (try 2/3)
Sep 12 13:23:34 x230 kernel: [ 3598.732029] wlan0: direct probe to d8:c7:c8:a1:c1:e0 (try 3/3)
Sep 12 13:23:34 x230 kernel: [ 3598.931753] wlan0: direct probe to d8:c7:c8:a1:c1:e0 timed out
Sep 12 13:23:43 x230 wpa_supplicant[6914]: Trying to authenticate with d8:c7:c8:a1:c1:e0 (SSID='bucknell.edu' freq=2412 MHz)
Sep 12 13:23:43 x230 kernel: [ 3607.128949] wlan0: authenticate with d8:c7:c8:a1:c1:e0 (try 1)
Sep 12 13:23:43 x230 kernel: [ 3607.130746] wlan0: d8:c7:c8:a1:c1:e0 denied authentication (status 17)
Sep 12 13:23:57 x230 NetworkManager[912]: <warn> Activation (wlan0/wireless): association took too long.
Sep 12 13:23:57 x230 NetworkManager[912]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 12 13:23:57 x230 NetworkManager[912]: <warn> Activation (wlan0/wireless): asking for new secrets
Sep 12 13:23:57 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep 12 13:24:00 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 12 13:24:00 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 12 13:24:00 x230 NetworkManager[912]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 12 13:24:00 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 12 13:24:00 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 12 13:24:00 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 12 13:24:00 x230 NetworkManager[912]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 12 13:24:00 x230 NetworkManager[912]: <info> Activation (wlan0/wireless): connection 'bucknell.edu' has security, and secrets exist.  No new secrets needed.
Sep 12 13:24:00 x230 NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 12 13:24:00 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 12 13:24:03 x230 wpa_supplicant[6914]: Trying to authenticate with d8:c7:c8:a1:c1:e0 (SSID='bucknell.edu' freq=2412 MHz)
Sep 12 13:24:03 x230 NetworkManager[912]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 12 13:24:03 x230 kernel: [ 3627.378256] wlan0: authenticate with d8:c7:c8:a1:c1:e0 (try 1)
Sep 12 13:24:03 x230 kernel: [ 3627.380139] wlan0: d8:c7:c8:a1:c1:e0 denied authentication (status 17)

```

---

### Post by chili555 on 2012-09-12
> **rfporto said:**
> I have the same laptop and configuration, with the newest kernel for 12.04 and I am having the same problem.  I too have disabled power management as well as wireless n, but the problem still persists.  Everything works fantastically on my home router, the only times I have issues are when I am on my college's wifi.Did you try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```This is temporary and will disappear on reboot unless we write one quick file.

---

### Post by rfporto on 2012-09-13
> **chili555 said:**
> Did you try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```This is temporary and will disappear on reboot unless we write one quick file.

Yes, I have tried, it does not fix the issue.  When I am connected via chrome (I have used firefox also, problem is there with that as well) I surf and eventually it just says sending request.  I check the network information and speed goes to unknown.  Network manager shows me as connected, but I am not.  Sometimes I am able to disconnect and reconnect, but it to eventually does the same, usually within a minute or two.  Eventually the network manager symbol on the upper right-hand corner goes grey and still shows me as connected to the network, but I cannot actually go online.

---

### Post by Earsplit on 2012-09-13
> **chili555 said:**
> Did you try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```This is temporary and will disappear on reboot unless we write one quick file.

Yes, as stated in the first post. I tried a variety of different modprobe parameters. rfporto has explained the situation very well.

I also tried disabling network manager on startup and replacing it with wicd. The same problems exist, which leads me to believe this is a problem with the iwlwifi driver itself.

Edit:

Just got connected and captured a log of a typical disconnect:
```


Sep 13 23:59:56 x230 wpa_supplicant[13582]: Trying to authenticate with d8:c7:c8:a1:c1:e8 (SSID='bucknell.edu' freq=5785 MHz)
Sep 13 23:59:56 x230 kernel: [14903.379011] wlan0: authenticate with d8:c7:c8:a1:c1:e8 (try 1)
Sep 13 23:59:57 x230 wpa_supplicant[13582]: Trying to associate with d8:c7:c8:a1:c1:e8 (SSID='bucknell.edu' freq=5785 MHz)
Sep 13 23:59:57 x230 kernel: [14903.576066] wlan0: authenticate with d8:c7:c8:a1:c1:e8 (try 2)
Sep 13 23:59:57 x230 kernel: [14903.577325] wlan0: authenticated
Sep 13 23:59:57 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 13 23:59:57 x230 kernel: [14903.669872] wlan0: associate with d8:c7:c8:a1:c1:e8 (try 1)
Sep 13 23:59:57 x230 kernel: [14903.867698] wlan0: associate with d8:c7:c8:a1:c1:e8 (try 2)
Sep 13 23:59:57 x230 kernel: [14903.869836] wlan0: RX AssocResp from d8:c7:c8:a1:c1:e8 (capab=0x411 status=0 aid=1)
Sep 13 23:59:57 x230 kernel: [14903.869842] wlan0: associated
Sep 13 23:59:57 x230 wpa_supplicant[13582]: Associated with d8:c7:c8:a1:c1:e8
Sep 13 23:59:57 x230 kernel: [14903.878169] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 13 23:59:57 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: associating -> associated
Sep 13 23:59:58 x230 wpa_supplicant[13582]: CTRL-EVENT-EAP-STARTED EAP authentication started
Sep 13 23:59:58 x230 wpa_supplicant[13582]: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
Sep 13 23:59:58 x230 wpa_supplicant[13582]: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
Sep 13 23:59:58 x230 wpa_supplicant[13582]: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/C=US/O=GeoTrust, Inc./CN=RapidSSL CA'
Sep 13 23:59:58 x230 wpa_supplicant[13582]: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/C=US/O=GeoTrust, Inc./CN=RapidSSL CA'
Sep 13 23:59:58 x230 wpa_supplicant[13582]: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='/serialNumber=R7fg4kbBEqEKtgm508TOlkrUDKckWGDi/C=US/O=auth.bucknell.edu/OU=GT00737013/OU=See www.rapidssl.com/resources/cps (c)11/OU=Domain Control Validated - RapidSSL(R)/CN=auth.bucknell.edu'
Sep 13 23:59:58 x230 wpa_supplicant[13582]: EAP-MSCHAPV2: Authentication succeeded
Sep 13 23:59:58 x230 wpa_supplicant[13582]: EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
Sep 13 23:59:58 x230 wpa_supplicant[13582]: CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
Sep 13 23:59:58 x230 wpa_supplicant[13582]: WPA: Key negotiation completed with d8:c7:c8:a1:c1:e8 [PTK=CCMP GTK=CCMP]
Sep 13 23:59:58 x230 wpa_supplicant[13582]: CTRL-EVENT-CONNECTED - Connection to d8:c7:c8:a1:c1:e8 completed (auth) [id=0 id_str=]
Sep 13 23:59:58 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: associated -> completed
Sep 13 23:59:58 x230 NetworkManager[934]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'bucknell.edu'.
Sep 13 23:59:58 x230 NetworkManager[934]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 13 23:59:58 x230 NetworkManager[934]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 13 23:59:58 x230 NetworkManager[934]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 13 23:59:58 x230 NetworkManager[934]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 13 23:59:58 x230 NetworkManager[934]: <info> Activation (wlan0) Beginning IP6 addrconf.
Sep 13 23:59:58 x230 NetworkManager[934]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 13 23:59:58 x230 NetworkManager[934]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 13 23:59:58 x230 dhclient: Listening on LPF/wlan0/24:77:03:73:0a:14
Sep 13 23:59:58 x230 dhclient: Sending on   LPF/wlan0/24:77:03:73:0a:14
Sep 13 23:59:58 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep 13 23:59:59 x230 dhclient: DHCPREQUEST of 134.82.119.248 on wlan0 to 255.255.255.255 port 67
Sep 13 23:59:59 x230 NetworkManager[934]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Sep 13 23:59:59 x230 NetworkManager[934]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 13 23:59:59 x230 NetworkManager[934]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep 13 23:59:59 x230 avahi-daemon[946]: Joining mDNS multicast group on interface wlan0.IPv4 with address 134.82.119.248.
Sep 13 23:59:59 x230 avahi-daemon[946]: New relevant interface wlan0.IPv4 for mDNS.
Sep 13 23:59:59 x230 avahi-daemon[946]: Registering new address record for 134.82.119.248 on wlan0.IPv4.
Sep 13 23:59:59 x230 avahi-daemon[946]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::2677:3ff:fe73:a14.
Sep 13 23:59:59 x230 avahi-daemon[946]: New relevant interface wlan0.IPv6 for mDNS.
Sep 13 23:59:59 x230 avahi-daemon[946]: Registering new address record for fe80::2677:3ff:fe73:a14 on wlan0.*.
Sep 14 00:00:00 x230 NetworkManager[934]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep 14 00:00:01 x230 NetworkManager[934]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep 14 00:00:01 x230 NetworkManager[934]: <info> (wlan0): roamed from BSSID D8:C7:C8:A1:BC:00 (bucknell.edu) to D8:C7:C8:A1:C1:E8 (bucknell.edu)
Sep 14 00:00:01 x230 NetworkManager[934]: <info> Policy set 'bucknell.edu' (wlan0) as default for IPv4 routing and DNS.
Sep 14 00:00:01 x230 NetworkManager[934]: <info> Activation (wlan0) successful, device activated.
Sep 14 00:00:01 x230 NetworkManager[934]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 14 00:00:05 x230 kernel: [14912.130193] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:a1:c1:e8 tid = 0
Sep 14 00:00:08 x230 kernel: [14915.224973] wlan0: no IPv6 routers present
Sep 14 00:00:18 x230 NetworkManager[934]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 14 00:00:18 x230 NetworkManager[934]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 14 00:00:18 x230 NetworkManager[934]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 14 00:00:18 x230 NetworkManager[934]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 14 00:00:33 x230 wpa_supplicant[13582]: Trying to authenticate with d8:c7:c8:a1:c8:e0 (SSID='bucknell.edu' freq=2462 MHz)
Sep 14 00:00:33 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 14 00:00:33 x230 kernel: [14940.484126] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 1/3)
Sep 14 00:00:34 x230 kernel: [14940.680190] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 2/3)
Sep 14 00:00:34 x230 kernel: [14940.880030] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 3/3)
Sep 14 00:00:34 x230 kernel: [14941.079870] wlan0: direct probe to d8:c7:c8:a1:c8:e0 timed out
Sep 14 00:00:46 x230 kernel: [14952.475387] wlan0: deauthenticating from d8:c7:c8:a1:c1:e8 by local choice (reason=2)
Sep 14 00:00:46 x230 wpa_supplicant[13582]: Trying to authenticate with d8:c7:c8:a1:c1:e8 (SSID='bucknell.edu' freq=5785 MHz)
Sep 14 00:00:46 x230 wpa_supplicant[13582]: CTRL-EVENT-DISCONNECTED bssid=d8:c7:c8:a1:c1:e8 reason=2
Sep 14 00:00:46 x230 kernel: [14952.590322] wlan0: authenticate with d8:c7:c8:a1:c1:e8 (try 1)
Sep 14 00:00:46 x230 wpa_supplicant[13582]: Trying to associate with d8:c7:c8:a1:c1:e8 (SSID='bucknell.edu' freq=5785 MHz)
Sep 14 00:00:46 x230 kernel: [14952.591447] wlan0: authenticated
Sep 14 00:00:46 x230 kernel: [14952.591823] wlan0: associate with d8:c7:c8:a1:c1:e8 (try 1)
Sep 14 00:00:46 x230 kernel: [14952.593618] wlan0: RX ReassocResp from d8:c7:c8:a1:c1:e8 (capab=0x411 status=0 aid=1)
Sep 14 00:00:46 x230 kernel: [14952.593622] wlan0: associated
Sep 14 00:00:46 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 14 00:00:46 x230 wpa_supplicant[13582]: Associated with d8:c7:c8:a1:c1:e8
Sep 14 00:00:46 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: associating -> associated
Sep 14 00:00:47 x230 wpa_supplicant[13582]: WPA: Key negotiation completed with d8:c7:c8:a1:c1:e8 [PTK=CCMP GTK=CCMP]
Sep 14 00:00:47 x230 wpa_supplicant[13582]: CTRL-EVENT-CONNECTED - Connection to d8:c7:c8:a1:c1:e8 completed (reauth) [id=0 id_str=]
Sep 14 00:00:47 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: associated -> completed
Sep 14 00:02:41 x230 kernel: [15067.664641] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:a1:c1:e8 tid = 0
Sep 14 00:02:49 x230 wpa_supplicant[13582]: Trying to authenticate with d8:c7:c8:a1:c8:e0 (SSID='bucknell.edu' freq=2462 MHz)
Sep 14 00:02:49 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 14 00:02:49 x230 kernel: [15076.069185] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 1/3)
Sep 14 00:02:49 x230 kernel: [15076.075223] wlan0: direct probe responded
Sep 14 00:02:49 x230 kernel: [15076.075318] wlan0: authenticate with d8:c7:c8:a1:c8:e0 (try 1)
Sep 14 00:02:49 x230 kernel: [15076.078373] wlan0: d8:c7:c8:a1:c8:e0 denied authentication (status 17)
Sep 14 00:03:25 x230 kernel: [15112.326430] wlan0: deauthenticating from d8:c7:c8:a1:c1:e8 by local choice (reason=2)
Sep 14 00:03:26 x230 wpa_supplicant[13582]: Trying to authenticate with d8:c7:c8:a1:c8:e0 (SSID='bucknell.edu' freq=2462 MHz)
Sep 14 00:03:26 x230 wpa_supplicant[13582]: CTRL-EVENT-DISCONNECTED bssid=d8:c7:c8:a1:c8:e0 reason=2
Sep 14 00:03:26 x230 kernel: [15112.485186] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 1/3)
Sep 14 00:03:26 x230 kernel: [15112.683730] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 2/3)
Sep 14 00:03:26 x230 NetworkManager[934]: <info> (wlan0): roamed from BSSID D8:C7:C8:A1:C1:E8 (bucknell.edu) to (none) ((none))
Sep 14 00:03:26 x230 kernel: [15112.883604] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 3/3)
Sep 14 00:03:26 x230 kernel: [15113.083453] wlan0: direct probe to d8:c7:c8:a1:c8:e0 timed out
Sep 14 00:03:28 x230 dhclient: Listening on LPF/wlan0/24:77:03:73:0a:14
Sep 14 00:03:28 x230 dhclient: Sending on   LPF/wlan0/24:77:03:73:0a:14
Sep 14 00:03:28 x230 dhclient: DHCPRELEASE on wlan0 to 172.20.2.2 port 67
Sep 14 00:03:28 x230 avahi-daemon[946]: Withdrawing address record for 134.82.119.248 on wlan0.
Sep 14 00:03:28 x230 avahi-daemon[946]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 134.82.119.248.
Sep 14 00:03:28 x230 avahi-daemon[946]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep 14 00:03:28 x230 avahi-daemon[946]: Interface wlan0.IPv6 no longer relevant for mDNS.
Sep 14 00:03:28 x230 avahi-daemon[946]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::2677:3ff:fe73:a14.
Sep 14 00:03:28 x230 avahi-daemon[946]: Withdrawing address record for fe80::2677:3ff:fe73:a14 on wlan0.
Sep 14 00:03:28 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 14 00:03:28 x230 wpa_supplicant[13582]: Trying to authenticate with d8:c7:c8:a1:c1:e0 (SSID='bucknell.edu' freq=2412 MHz)
Sep 14 00:03:28 x230 wpa_supplicant[13582]: Authentication request to the driver failed
Sep 14 00:03:28 x230 kernel: [15115.131295] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
Sep 14 00:03:28 x230 kernel: [15115.138067] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
Sep 14 00:03:28 x230 kernel: [15115.314984] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 14 00:03:29 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 14 00:03:29 x230 NetworkManager[934]: <info> wpa_supplicant stopped
Sep 14 00:03:29 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: authenticating -> down
Sep 14 00:03:29 x230 NetworkManager[934]: <info> (wlan0): device state change: activated -> unavailable (reason 'supplicant-failed') [100 20 10]
Sep 14 00:03:29 x230 dbus[889]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Sep 14 00:03:29 x230 dbus[889]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Sep 14 00:03:29 x230 NetworkManager[934]: <info> (wlan0): deactivating device (reason 'supplicant-failed') [10]
Sep 14 00:03:29 x230 NetworkManager[934]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 13908
Sep 14 00:03:29 x230 NetworkManager[934]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep 14 00:03:29 x230 kernel: [15115.961551] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by chili555 on 2012-09-14
> The same problems exist, which leads me to believe this is a problem with the iwlwifi driver itself.I'm not sure I quite agree:>  <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 14 00:00:46 x230 wpa_supplicant[13582]: [COLOR="Red"]Associated with d8:c7:c8:a1:c1:**e8**[/COLOR]
Sep 14 00:00:46 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: associating -> associated
Sep 14 00:00:47 x230 wpa_supplicant[13582]: WPA: Key negotiation completed with d8:c7:c8:a1:c1:e8 [PTK=CCMP GTK=CCMP]
Sep 14 00:00:47 x230 wpa_supplicant[13582]: CTRL-EVENT-CONNECTED - Connection to d8:c7:c8:a1:c1:e8 completed (reauth) [id=0 id_str=]
Sep 14 00:00:47 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: associated -> completed
Sep 14 00:02:41 x230 kernel: [15067.664641] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:a1:c1:e8 tid = 0
Sep 14 00:02:49 x230 wpa_supplicant[13582]: [COLOR="Red"]Trying to authenticate with d8:c7:c8:a1:c8:**e0**[/COLOR] (SSID='bucknell.edu' freq=2462 MHz)
Sep 14 00:02:49 x230 NetworkManager[934]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 14 00:02:49 x230 kernel: [15076.069185] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 1/3)
Sep 14 00:02:49 x230 kernel: [15076.075223] wlan0: direct probe responded
Sep 14 00:02:49 x230 kernel: [15076.075318] wlan0: authenticate with d8:c7:c8:a1:c8:e0 (try 1)
Sep 14 00:02:49 x230 kernel: [15076.078373] [COLOR="Red"]wlan0: d8:c7:c8:a1:c8:e0 denied authentication (status 17)[/COLOR]
Sep 14 00:03:25 x230 kernel: [15112.326430] wlan0: deauthenticating from d8:c7:c8:a1:c1:e8 by local choice (reason=2)
Sep 14 00:03:26 x230 wpa_supplicant[13582]: Trying to authenticate with d8:c7:c8:a1:c8:e0 (SSID='bucknell.edu' freq=2462 MHz)
Sep 14 00:03:26 x230 wpa_supplicant[13582]: CTRL-EVENT-DISCONNECTED bssid=d8:c7:c8:a1:c8:e0 reason=2
Sep 14 00:03:26 x230 kernel: [15112.485186] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 1/3)
Sep 14 00:03:26 x230 kernel: [15112.683730] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 2/3)
Sep 14 00:03:26 x230 NetworkManager[934]: [COLOR="Red"]<info> (wlan0): roamed from BSSID D8:C7:C8:A1:C1:E8 (bucknell.edu) to (none) ((none))[/COLOR]
Sep 14 00:03:26 x230 kernel: [15112.883604] wlan0: direct probe to d8:c7:c8:a1:c8:e0 (try 3/3)
Sep 14 00:03:26 x230 kernel: [15113.083453] wlan0: direct probe to d8:c7:c8:a1:c8:e0 timed outSo we see the card roaming from one SSID, where it holds credentials and authenticates perfectly well, to another identically named SSID for which it does not hold credentials and gets rejected. That's pretty clearly a Network Manager or Wicd issue.

We need to find a way to get associated with d8:c7:c8:a1:c1:e8 (SSID='bucknell.edu') and hold.

Googling for 'iwlwifi and disable roaming' and I suggest you do as well.> I also tried disabling network manager on startup and replacing it with wicd.I doubt this will be effective. Didn't re-spawn like the vicious alien it is?```
ps aux | grep -i network
```

---

### Post by chili555 on 2012-09-14
We might build compat-wireless and invoke 5ghz_disable=1, or is it the 5 Ghz channel that you need?

Reference:```
# modinfo drivers/net/wireless/iwlwifi/iwlwifi.ko
filename:       drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     6D93FF34E4CED193F6EC4F7
<snip>
depends:        mac80211,cfg80211,compat
vermagic:       3.2.0-30-generic-pae SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
[COLOR="Red"]parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)[/COLOR]

```I'm a bit confused because the parameter says default is 0 which is an integer but the modinfo says the change is boolean. Boolean implies Y or N.

:confused:

[https://bugzilla.redhat.com/show_bug.cgi?id=812259](https://bugzilla.redhat.com/show_bug.cgi?id=812259)

---

### Post by rfporto on 2012-09-14
> **chili555 said:**
> We might build compat-wireless and invoke 5ghz_disable=1, or is it the 5 Ghz channel that you need?

Reference:```
# modinfo drivers/net/wireless/iwlwifi/iwlwifi.ko
filename:       drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     6D93FF34E4CED193F6EC4F7
<snip>
depends:        mac80211,cfg80211,compat
vermagic:       3.2.0-30-generic-pae SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
[COLOR="Red"]parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)[/COLOR]

```I'm a bit confused because the parameter says default is 0 which is an integer but the modinfo says the change is boolean. Boolean implies Y or N.

:confused:

[https://bugzilla.redhat.com/show_bug.cgi?id=812259](https://bugzilla.redhat.com/show_bug.cgi?id=812259)

I am not sure if I need 5ghz, do you know how to create a code, much like the disable n, that will reset on reboot so that I can test?

---

### Post by chili555 on 2012-09-14
> **rfporto said:**
> I am not sure if I need 5ghz, do you know how to create a code, much like the disable n, that will reset on reboot so that I can test?Not in the current driver. That's why I suggested we compile a newer version; one that contains the ability to do so temporarily and, if it's helpful, permanently.

---

### Post by rfporto on 2012-09-14
> **chili555 said:**
> Not in the current driver. That's why I suggested we compile a newer version; one that contains the ability to do so temporarily and, if it's helpful, permanently.

I'll test, thank you so much.  Please walk me through the steps, I am very new to linux, in fact this is the first machine I have had that runs it.

---

### Post by chili555 on 2012-09-14
> I also tried disabling network manager on startup and replacing it with wicd. I actually think there is a good chance Wicd will work better, but not with Network Manager installed and probably running. Before we do radical surgery, let's try Wicd by removing NM:```
sudo apt-get remove --purge network-manager
```Reboot and click on your desired network in Wicd. Is there any improvement?

We'll proceed further if needed.

---

### Post by rfporto on 2012-09-14
> **chili555 said:**
> I actually think there is a good chance Wicd will work better, but not with Network Manager installed and probably running. Before we do radical surgery, let's try Wicd by removing NM:```
sudo apt-get remove --purge network-manager
```Reboot and click on your desired network in Wicd. Is there any improvement?

We'll proceed further if needed.

Is Wicd something that needs to be installed?  I have not done so if it does, that was Earsplit.

---

### Post by chili555 on 2012-09-14
> **rfporto said:**
> Is Wicd something that needs to be installed?  I have not done so if it does, that was Earsplit.Oops,sorry about that. Unless you are feeling especially adventuresome, we'd better check your logs as with Earsplit to see if 5ghz and roaming is really your issue. With the ethernet disconnected, please run and post:```
sudo cat /var/log/syslog | grep -e etwork -e wlan -e wpa
```

---

### Post by rfporto on 2012-09-14
> **chili555 said:**
> Oops,sorry about that. Unless you are feeling especially adventuresome, we'd better check your logs as with Earsplit to see if 5ghz and roaming is really your issue. With the ethernet disconnected, please run and post:```
sudo cat /var/log/syslog | grep -e etwork -e wlan -e wpa
```

I'm sorry, I am actually out of town for the weekend, I will not be able to get back on that network until Monday.  Hopefully Earsplit will work with you, and I will be back shortly.  Again, thank you so much for helping Chili555, might need to send a few beers to South Carolina.

---

### Post by Earsplit on 2012-09-17
With network-manager purged and wicd installed, I'm getting worse luck. See the log files below.

Thanks for your help so far. I too was away this weekend.


On a WPA2 enterprise network with TKIP/MSCHAPV2 and PEAP
```

sudo cat /var/log/syslog | grep -e etwork -e wlan -e wpa

Sep 17 16:31:59 x230 dhclient: Listening on LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:31:59 x230 dhclient: Sending on   LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:31:59 x230 dhclient: DHCPRELEASE on wlan0 to 10.101.0.254 port 67
Sep 17 16:31:59 x230 dhclient: send_packet: Network is unreachable
Sep 17 16:31:59 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 17 16:31:59 x230 kernel: [  823.968179] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 17 16:31:59 x230 kernel: [  824.020162] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 1/3)
Sep 17 16:31:59 x230 dhclient: send_packet: Network is unreachable
Sep 17 16:31:59 x230 kernel: [  824.217856] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 2/3)
Sep 17 16:32:00 x230 kernel: [  824.417531] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 3/3)
Sep 17 16:32:00 x230 dhclient: receive_packet failed on eth0: Network is down
Sep 17 16:32:00 x230 kernel: [  824.617184] wlan0: direct probe to d8:c7:c8:a1:c1:e1 timed out
Sep 17 16:32:00 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 17 16:32:00 x230 dhclient: Listening on LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:32:00 x230 dhclient: Sending on   LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:32:00 x230 dhclient: DHCPRELEASE on wlan0 to 10.101.0.254 port 67
Sep 17 16:32:00 x230 dhclient: send_packet: Network is unreachable
Sep 17 16:32:00 x230 kernel: [  825.193937] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 17 16:32:00 x230 kernel: [  825.252186] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 1/3)
Sep 17 16:32:01 x230 kernel: [  825.451748] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 2/3)
Sep 17 16:32:01 x230 kernel: [  825.651378] wlan0: direct probe to d8:c7:c8:a1:c1:e1 (try 3/3)
Sep 17 16:32:01 x230 kernel: [  825.850960] wlan0: direct probe to d8:c7:c8:a1:c1:e1 timed out
Sep 17 16:32:03 x230 kernel: [  827.260437] wlan0: deauthenticating from d8:c7:c8:a1:b9:d1 by local choice (reason=3)
Sep 17 16:32:40 x230 dhclient: Listening on LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:32:40 x230 dhclient: Sending on   LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:32:40 x230 dhclient: DHCPRELEASE on wlan0 to 10.101.0.254 port 67
Sep 17 16:32:40 x230 dhclient: send_packet: Network is unreachable
Sep 17 16:32:40 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 17 16:32:40 x230 kernel: [  865.123669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 17 16:32:41 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 17 16:32:41 x230 dhclient: send_packet: Network is unreachable

```

Same thing attempted on an open (unencrypted) guest network
```

Sep 17 16:34:24 x230 dhclient: Listening on LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:34:24 x230 dhclient: Sending on   LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:34:24 x230 dhclient: DHCPRELEASE on wlan0 to 10.101.0.254 port 67
Sep 17 16:34:24 x230 dhclient: send_packet: Network is unreachable
Sep 17 16:34:24 x230 kernel: [  968.798801] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 17 16:34:24 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 17 16:34:25 x230 kernel: [  969.055565] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 17 16:34:25 x230 dhclient: send_packet: Network is unreachable
Sep 17 16:34:25 x230 dhclient: receive_packet failed on eth0: Network is down
Sep 17 16:34:25 x230 dhclient: receive_packet failed on wlan0: Network is down
Sep 17 16:34:25 x230 dhclient: Listening on LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:34:25 x230 dhclient: Sending on   LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:34:25 x230 dhclient: DHCPRELEASE on wlan0 to 10.101.0.254 port 67
Sep 17 16:34:25 x230 dhclient: send_packet: Network is unreachable
Sep 17 16:34:26 x230 kernel: [  970.226159] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 17 16:34:28 x230 dhclient: Listening on LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:34:28 x230 dhclient: Sending on   LPF/wlan0/24:77:03:73:0a:14
Sep 17 16:34:28 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep 17 16:34:28 x230 kernel: [  972.411487] wlan0: direct probe to d8:c7:c8:a1:c8:e1 (try 1/3)
Sep 17 16:34:28 x230 kernel: [  972.607686] wlan0: direct probe to d8:c7:c8:a1:c8:e1 (try 2/3)
Sep 17 16:34:28 x230 kernel: [  972.807272] wlan0: direct probe to d8:c7:c8:a1:c8:e1 (try 3/3)
Sep 17 16:34:29 x230 kernel: [  973.006903] wlan0: direct probe to d8:c7:c8:a1:c8:e1 timed out
Sep 17 16:34:31 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Sep 17 16:34:37 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Sep 17 16:34:43 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Sep 17 16:34:55 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Sep 17 16:35:10 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Sep 17 16:35:26 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Sep 17 16:35:33 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Sep 17 16:35:47 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Sep 17 16:35:58 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Sep 17 16:36:17 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Sep 17 16:36:21 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep 17 16:36:24 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Sep 17 16:36:32 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Sep 17 16:36:37 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Sep 17 16:36:43 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Sep 17 16:36:44 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Sep 17 16:36:52 x230 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11

```

---

### Post by chili555 on 2012-09-18
> With network-manager purged and wicd installed, I'm getting worse luck. See the log files below.Indeed. You might find more useful information in:```
sudo cat /var/log/wicd/wicd.log
``` TKIP/MSCHAPV2 and PEAP is *very* challenging.

---

### Post by rfporto on 2012-09-18
) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info> dhclient started with pid 2622
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info> Activation (wlan0) Beginning IP6 addrconf.
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 18 12:22:08 ryan-ThinkPad-X230 avahi-daemon[700]: Withdrawing address record for fe80::2677:3ff:fe71:38b0 on wlan0.
Sep 18 12:22:08 ryan-ThinkPad-X230 avahi-daemon[700]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::2677:3ff:fe71:38b0.
Sep 18 12:22:08 ryan-ThinkPad-X230 avahi-daemon[700]: Interface wlan0.IPv6 no longer relevant for mDNS.
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 18 12:22:08 ryan-ThinkPad-X230 dhclient: Listening on LPF/wlan0/24:77:03:71:38:b0
Sep 18 12:22:08 ryan-ThinkPad-X230 dhclient: Sending on   LPF/wlan0/24:77:03:71:38:b0
Sep 18 12:22:08 ryan-ThinkPad-X230 dhclient: DHCPREQUEST of 129.8.201.219 on wlan0 to 255.255.255.255 port 67
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info>   address 129.8.201.219
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info>   prefix 24 (255.255.255.0)
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info>   gateway 129.8.201.1
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info>   hostname 'ryan-ThinkPad-X230'
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info>   nameserver '129.8.15.50'
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info>   nameserver '129.8.247.50'
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info>   domain name 'wnet.csufresno.edu'
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info>   wins '129.8.15.59'
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info>   wins '129.8.247.59'
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 18 12:22:08 ryan-ThinkPad-X230 NetworkManager[967]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep 18 12:22:08 ryan-ThinkPad-X230 avahi-daemon[700]: Joining mDNS multicast group on interface wlan0.IPv4 with address 129.8.201.219.
Sep 18 12:22:08 ryan-ThinkPad-X230 avahi-daemon[700]: New relevant interface wlan0.IPv4 for mDNS.
Sep 18 12:22:08 ryan-ThinkPad-X230 avahi-daemon[700]: Registering new address record for 129.8.201.219 on wlan0.IPv4.
Sep 18 12:22:09 ryan-ThinkPad-X230 NetworkManager[967]: <info> DNS: starting dnsmasq...
Sep 18 12:22:09 ryan-ThinkPad-X230 NetworkManager[967]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep 18 12:22:09 ryan-ThinkPad-X230 NetworkManager[967]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep 18 12:22:09 ryan-ThinkPad-X230 NetworkManager[967]: <info> (wlan0): roamed from BSSID 00:0B:86:ED:55:F0 (bulldogs) to (none) ((none))
Sep 18 12:22:09 ryan-ThinkPad-X230 NetworkManager[967]: <info> Policy set 'bulldogs' (wlan0) as default for IPv4 routing and DNS.
Sep 18 12:22:09 ryan-ThinkPad-X230 NetworkManager[967]: <info> Activation (wlan0) successful, device activated.
Sep 18 12:22:09 ryan-ThinkPad-X230 NetworkManager[967]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 18 12:22:09 ryan-ThinkPad-X230 avahi-daemon[700]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::2677:3ff:fe71:38b0.
Sep 18 12:22:09 ryan-ThinkPad-X230 avahi-daemon[700]: New relevant interface wlan0.IPv6 for mDNS.
Sep 18 12:22:09 ryan-ThinkPad-X230 avahi-daemon[700]: Registering new address record for fe80::2677:3ff:fe71:38b0 on wlan0.*.
Sep 18 12:22:17 ryan-ThinkPad-X230 wpa_supplicant[1322]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:22:17 ryan-ThinkPad-X230 kernel: [  491.307323] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:22:17 ryan-ThinkPad-X230 NetworkManager[967]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 18 12:22:17 ryan-ThinkPad-X230 kernel: [  491.351327] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:22:17 ryan-ThinkPad-X230 kernel: [  491.554801] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:22:17 ryan-ThinkPad-X230 kernel: [  491.758279] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:22:17 ryan-ThinkPad-X230 kernel: [  491.961754] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:22:18 ryan-ThinkPad-X230 kernel: [  492.783660] wlan0: no IPv6 routers present
Sep 18 12:22:25 ryan-ThinkPad-X230 wpa_supplicant[1322]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:22:25 ryan-ThinkPad-X230 kernel: [  500.210471] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:22:26 ryan-ThinkPad-X230 kernel: [  500.223541] wlan0: send auth to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:22:26 ryan-ThinkPad-X230 kernel: [  500.227870] wlan0: 00:0b:86:ed:55:e0 denied authentication (status 17)
Sep 18 12:22:28 ryan-ThinkPad-X230 NetworkManager[967]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 18 12:22:28 ryan-ThinkPad-X230 NetworkManager[967]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 18 12:22:28 ryan-ThinkPad-X230 NetworkManager[967]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 18 12:22:28 ryan-ThinkPad-X230 NetworkManager[967]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 18 12:22:44 ryan-ThinkPad-X230 kernel: [    1.986987] e1000e: Intel(R) PRO/1000 Network Driver - 1.9.5-k
Sep 18 12:22:44 ryan-ThinkPad-X230 kernel: [    2.239173] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Sep 18 12:22:45 ryan-ThinkPad-X230 kernel: [    2.513398] type=1400 audit(1347996165.019:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=619 comm="apparmor_parser"
Sep 18 12:22:45 ryan-ThinkPad-X230 avahi-daemon[625]: Network interface enumeration completed.
Sep 18 12:22:45 ryan-ThinkPad-X230 kernel: [    2.664073] type=1400 audit(1347996165.167:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=931 comm="apparmor_parser"
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> NetworkManager (version 0.9.4.0) is starting...
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> DNS: loaded plugin dnsmasq
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: init!
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: update_system_hostname
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPluginIfupdown: management mode: unmanaged
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: end _init.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    Ifupdown: get unmanaged devices count: 0
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: (9093936) ... get_connections.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    SCPlugin-Ifupdown: (9093936) ... get_connections (managed=false): return empty list.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile: parsing Porto Wi Fi ... 
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile:     read connection 'Porto Wi Fi'
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile: parsing SEC_LinkShare_048301 ... 
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile:     read connection 'SEC_LinkShare_048301'
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile: parsing NETGEAR ... 
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile:     read connection 'NETGEAR'
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile: parsing 2WIRE177 ... 
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile:     read connection '2WIRE177'
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile: parsing bulldogs ... 
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    keyfile:     read connection 'bulldogs'
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]:    Ifupdown: get unmanaged devices count: 0
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> modem-manager is now available
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill2) (driver (unknown))
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> Networking is enabled by state file
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <warn> failed to allocate link cache: (-10) Operation not supported
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (eth0): carrier is OFF
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (eth0): new Ethernet device (driver: 'e1000e' ifindex: 2)
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (eth0): now managed
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (eth0): bringing up device.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (eth0): preparing device.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (eth0): deactivating device (reason 'managed') [2]
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:19.0/net/eth0
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): using nl80211 for WiFi device control
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): now managed
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): bringing up device.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): preparing device.
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): deactivating device (reason 'managed') [2]
Sep 18 12:22:45 ryan-ThinkPad-X230 dbus[577]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Sep 18 12:22:45 ryan-ThinkPad-X230 kernel: [    3.359213] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 18 12:22:45 ryan-ThinkPad-X230 dbus[577]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> wpa_supplicant started
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: starting -> ready
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: ready -> inactive
Sep 18 12:22:45 ryan-ThinkPad-X230 NetworkManager[941]: <warn> Trying to remove a non-existant call id.
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Auto-activating connection 'bulldogs'.
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) starting connection 'bulldogs'
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0/wireless): connection 'bulldogs' requires no security.  No secrets needed.
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Config: added 'ssid' value 'bulldogs'
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Config: added 'scan_ssid' value '1'
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Config: added 'key_mgmt' value 'NONE'
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> Config: set interface ap_scan to 1
Sep 18 12:22:50 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: inactive -> scanning
Sep 18 12:22:53 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:22:53 ryan-ThinkPad-X230 kernel: [   10.944242] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:22:53 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 18 12:22:53 ryan-ThinkPad-X230 kernel: [   10.998759] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:22:53 ryan-ThinkPad-X230 kernel: [   11.202228] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:22:53 ryan-ThinkPad-X230 kernel: [   11.405704] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:22:54 ryan-ThinkPad-X230 kernel: [   11.609152] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:23:02 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:23:02 ryan-ThinkPad-X230 kernel: [   19.829768] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:23:02 ryan-ThinkPad-X230 kernel: [   19.840686] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:23:02 ryan-ThinkPad-X230 kernel: [   20.043523] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:23:02 ryan-ThinkPad-X230 kernel: [   20.247046] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:23:03 ryan-ThinkPad-X230 kernel: [   20.450479] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:23:11 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:23:11 ryan-ThinkPad-X230 kernel: [   28.613929] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:23:11 ryan-ThinkPad-X230 kernel: [   28.624729] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:23:11 ryan-ThinkPad-X230 kernel: [   28.825048] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:23:11 ryan-ThinkPad-X230 kernel: [   29.028513] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:23:11 ryan-ThinkPad-X230 kernel: [   29.231999] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:23:19 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:23:19 ryan-ThinkPad-X230 kernel: [   37.397744] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:23:20 ryan-ThinkPad-X230 kernel: [   37.409711] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:23:20 ryan-ThinkPad-X230 kernel: [   37.610514] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:23:20 ryan-ThinkPad-X230 kernel: [   37.813986] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:23:20 ryan-ThinkPad-X230 kernel: [   38.017423] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:23:28 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:23:28 ryan-ThinkPad-X230 kernel: [   46.018776] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:23:28 ryan-ThinkPad-X230 kernel: [   46.031812] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:23:28 ryan-ThinkPad-X230 kernel: [   46.232390] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:23:29 ryan-ThinkPad-X230 kernel: [   46.435837] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:23:29 ryan-ThinkPad-X230 kernel: [   46.639357] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:23:37 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:23:37 ryan-ThinkPad-X230 kernel: [   54.761280] wlan0: authenticate with 00:0b:86:ed:55:f0
Sep 18 12:23:37 ryan-ThinkPad-X230 kernel: [   54.802296] wlan0: send auth to 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:23:37 ryan-ThinkPad-X230 kernel: [   55.001875] wlan0: send auth to 00:0b:86:ed:55:f0 (try 2/3)
Sep 18 12:23:37 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to associate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:23:37 ryan-ThinkPad-X230 kernel: [   55.205373] wlan0: send auth to 00:0b:86:ed:55:f0 (try 3/3)
Sep 18 12:23:37 ryan-ThinkPad-X230 kernel: [   55.207337] wlan0: authenticated
Sep 18 12:23:37 ryan-ThinkPad-X230 kernel: [   55.209358] wlan0: associate with 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 18 12:23:37 ryan-ThinkPad-X230 kernel: [   55.212620] wlan0: RX AssocResp from 00:0b:86:ed:55:f0 (capab=0x401 status=0 aid=5)
Sep 18 12:23:37 ryan-ThinkPad-X230 kernel: [   55.212627] wlan0: associated
Sep 18 12:23:37 ryan-ThinkPad-X230 kernel: [   55.217167] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 18 12:23:37 ryan-ThinkPad-X230 wpa_supplicant[1279]: Associated with 00:0b:86:ed:55:f0
Sep 18 12:23:37 ryan-ThinkPad-X230 wpa_supplicant[1279]: CTRL-EVENT-CONNECTED - Connection to 00:0b:86:ed:55:f0 completed (auth) [id=0 id_str=]
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: associating -> completed
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'bulldogs'.
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> dhclient started with pid 1942
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Beginning IP6 addrconf.
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 18 12:23:37 ryan-ThinkPad-X230 dhclient: Listening on LPF/wlan0/24:77:03:71:38:b0
Sep 18 12:23:37 ryan-ThinkPad-X230 dhclient: Sending on   LPF/wlan0/24:77:03:71:38:b0
Sep 18 12:23:37 ryan-ThinkPad-X230 dhclient: DHCPREQUEST of 129.8.201.219 on wlan0 to 255.255.255.255 port 67
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   address 129.8.201.219
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   prefix 24 (255.255.255.0)
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   gateway 129.8.201.1
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   hostname 'ryan-ThinkPad-X230'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   nameserver '129.8.15.50'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   nameserver '129.8.247.50'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   domain name 'wnet.csufresno.edu'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   wins '129.8.15.59'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   wins '129.8.247.59'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep 18 12:23:37 ryan-ThinkPad-X230 avahi-daemon[625]: Joining mDNS multicast group on interface wlan0.IPv4 with address 129.8.201.219.
Sep 18 12:23:37 ryan-ThinkPad-X230 avahi-daemon[625]: New relevant interface wlan0.IPv4 for mDNS.
Sep 18 12:23:37 ryan-ThinkPad-X230 avahi-daemon[625]: Registering new address record for 129.8.201.219 on wlan0.IPv4.
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> DNS: starting dnsmasq...
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): roamed from BSSID 00:0B:86:ED:88:70 (bulldogs) to 00:0B:86:ED:55:F0 (bulldogs)
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> Policy set 'bulldogs' (wlan0) as default for IPv4 routing and DNS.
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) successful, device activated.
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 18 12:23:39 ryan-ThinkPad-X230 avahi-daemon[625]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::2677:3ff:fe71:38b0.
Sep 18 12:23:39 ryan-ThinkPad-X230 avahi-daemon[625]: New relevant interface wlan0.IPv6 for mDNS.
Sep 18 12:23:39 ryan-ThinkPad-X230 avahi-daemon[625]: Registering new address record for fe80::2677:3ff:fe71:38b0 on wlan0.*.
Sep 18 12:23:47 ryan-ThinkPad-X230 kernel: [   65.822122] wlan0: no IPv6 routers present
Sep 18 12:23:57 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 18 12:23:57 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 18 12:23:57 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 18 12:23:57 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 18 12:24:13 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:24:13 ryan-ThinkPad-X230 kernel: [   91.615589] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:24:13 ryan-ThinkPad-X230 kernel: [   91.659624] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:24:13 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 18 12:24:14 ryan-ThinkPad-X230 kernel: [   91.859337] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:24:14 ryan-ThinkPad-X230 kernel: [   92.062861] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:24:14 ryan-ThinkPad-X230 kernel: [   92.266294] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:24:22 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:24:22 ryan-ThinkPad-X230 kernel: [  100.417234] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:24:22 ryan-ThinkPad-X230 kernel: [  100.421044] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:24:22 ryan-ThinkPad-X230 kernel: [  100.620913] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:24:23 ryan-ThinkPad-X230 kernel: [  100.824345] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:24:23 ryan-ThinkPad-X230 kernel: [  101.027826] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:24:27 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): roamed from BSSID 00:0B:86:ED:55:F0 (bulldogs) to (none) ((none))
Sep 18 12:24:31 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.057998] wlan0: authenticate with 00:0b:86:ed:55:f0
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.089305] wlan0: send auth to 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.290677] wlan0: send auth to 00:0b:86:ed:55:f0 (try 2/3)
Sep 18 12:24:31 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to associate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.494110] wlan0: send auth to 00:0b:86:ed:55:f0 (try 3/3)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.495875] wlan0: authenticated
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.498182] wlan0: associate with 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:24:31 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.501271] wlan0: RX AssocResp from 00:0b:86:ed:55:f0 (capab=0x401 status=0 aid=5)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.501274] wlan0: associated
Sep 18 12:24:31 ryan-ThinkPad-X230 wpa_supplicant[1279]: Associated with 00:0b:86:ed:55:f0
Sep 18 12:24:31 ryan-ThinkPad-X230 wpa_supplicant[1279]: CTRL-EVENT-CONNECTED - Connection to 00:0b:86:ed:55:f0 completed (reauth) [id=0 id_str=]
Sep 18 12:24:31 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: associating -> completed

---

### Post by rfporto on 2012-09-18
Thats what I got while connected, will post when I get disconnected

---

### Post by rfporto on 2012-09-18
) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> dhclient started with pid 1942
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Beginning IP6 addrconf.
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 18 12:23:37 ryan-ThinkPad-X230 dhclient: Listening on LPF/wlan0/24:77:03:71:38:b0
Sep 18 12:23:37 ryan-ThinkPad-X230 dhclient: Sending on   LPF/wlan0/24:77:03:71:38:b0
Sep 18 12:23:37 ryan-ThinkPad-X230 dhclient: DHCPREQUEST of 129.8.201.219 on wlan0 to 255.255.255.255 port 67
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   address 129.8.201.219
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   prefix 24 (255.255.255.0)
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   gateway 129.8.201.1
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   hostname 'ryan-ThinkPad-X230'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   nameserver '129.8.15.50'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   nameserver '129.8.247.50'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   domain name 'wnet.csufresno.edu'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   wins '129.8.15.59'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info>   wins '129.8.247.59'
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 18 12:23:37 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep 18 12:23:37 ryan-ThinkPad-X230 avahi-daemon[625]: Joining mDNS multicast group on interface wlan0.IPv4 with address 129.8.201.219.
Sep 18 12:23:37 ryan-ThinkPad-X230 avahi-daemon[625]: New relevant interface wlan0.IPv4 for mDNS.
Sep 18 12:23:37 ryan-ThinkPad-X230 avahi-daemon[625]: Registering new address record for 129.8.201.219 on wlan0.IPv4.
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> DNS: starting dnsmasq...
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): roamed from BSSID 00:0B:86:ED:88:70 (bulldogs) to 00:0B:86:ED:55:F0 (bulldogs)
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> Policy set 'bulldogs' (wlan0) as default for IPv4 routing and DNS.
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) successful, device activated.
Sep 18 12:23:38 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 18 12:23:39 ryan-ThinkPad-X230 avahi-daemon[625]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::2677:3ff:fe71:38b0.
Sep 18 12:23:39 ryan-ThinkPad-X230 avahi-daemon[625]: New relevant interface wlan0.IPv6 for mDNS.
Sep 18 12:23:39 ryan-ThinkPad-X230 avahi-daemon[625]: Registering new address record for fe80::2677:3ff:fe71:38b0 on wlan0.*.
Sep 18 12:23:47 ryan-ThinkPad-X230 kernel: [   65.822122] wlan0: no IPv6 routers present
Sep 18 12:23:57 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 18 12:23:57 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 18 12:23:57 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 18 12:23:57 ryan-ThinkPad-X230 NetworkManager[941]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 18 12:24:13 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:24:13 ryan-ThinkPad-X230 kernel: [   91.615589] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:24:13 ryan-ThinkPad-X230 kernel: [   91.659624] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:24:13 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 18 12:24:14 ryan-ThinkPad-X230 kernel: [   91.859337] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:24:14 ryan-ThinkPad-X230 kernel: [   92.062861] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:24:14 ryan-ThinkPad-X230 kernel: [   92.266294] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:24:22 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:24:22 ryan-ThinkPad-X230 kernel: [  100.417234] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:24:22 ryan-ThinkPad-X230 kernel: [  100.421044] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:24:22 ryan-ThinkPad-X230 kernel: [  100.620913] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:24:23 ryan-ThinkPad-X230 kernel: [  100.824345] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:24:23 ryan-ThinkPad-X230 kernel: [  101.027826] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:24:27 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): roamed from BSSID 00:0B:86:ED:55:F0 (bulldogs) to (none) ((none))
Sep 18 12:24:31 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.057998] wlan0: authenticate with 00:0b:86:ed:55:f0
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.089305] wlan0: send auth to 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.290677] wlan0: send auth to 00:0b:86:ed:55:f0 (try 2/3)
Sep 18 12:24:31 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to associate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.494110] wlan0: send auth to 00:0b:86:ed:55:f0 (try 3/3)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.495875] wlan0: authenticated
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.498182] wlan0: associate with 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:24:31 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.501271] wlan0: RX AssocResp from 00:0b:86:ed:55:f0 (capab=0x401 status=0 aid=5)
Sep 18 12:24:31 ryan-ThinkPad-X230 kernel: [  109.501274] wlan0: associated
Sep 18 12:24:31 ryan-ThinkPad-X230 wpa_supplicant[1279]: Associated with 00:0b:86:ed:55:f0
Sep 18 12:24:31 ryan-ThinkPad-X230 wpa_supplicant[1279]: CTRL-EVENT-CONNECTED - Connection to 00:0b:86:ed:55:f0 completed (reauth) [id=0 id_str=]
Sep 18 12:24:31 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: associating -> completed
Sep 18 12:24:53 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:24:53 ryan-ThinkPad-X230 kernel: [  131.245705] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:24:53 ryan-ThinkPad-X230 kernel: [  131.289669] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:24:53 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 18 12:24:53 ryan-ThinkPad-X230 kernel: [  131.489701] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:24:53 ryan-ThinkPad-X230 kernel: [  131.693220] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:24:54 ryan-ThinkPad-X230 kernel: [  131.896666] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:25:02 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:25:02 ryan-ThinkPad-X230 kernel: [  140.001074] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:25:02 ryan-ThinkPad-X230 kernel: [  140.012125] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:25:02 ryan-ThinkPad-X230 kernel: [  140.215321] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:25:02 ryan-ThinkPad-X230 kernel: [  140.418797] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:25:02 ryan-ThinkPad-X230 kernel: [  140.622318] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:25:11 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:25:11 ryan-ThinkPad-X230 kernel: [  148.728907] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:25:11 ryan-ThinkPad-X230 kernel: [  148.732039] wlan0: send auth to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:25:11 ryan-ThinkPad-X230 kernel: [  148.734884] wlan0: 00:0b:86:ed:55:e0 denied authentication (status 17)
Sep 18 12:25:50 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:25:50 ryan-ThinkPad-X230 kernel: [  188.057227] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:25:50 ryan-ThinkPad-X230 kernel: [  188.069083] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:25:50 ryan-ThinkPad-X230 kernel: [  188.272113] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:25:50 ryan-ThinkPad-X230 kernel: [  188.475551] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:25:51 ryan-ThinkPad-X230 kernel: [  188.679057] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:25:59 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:25:59 ryan-ThinkPad-X230 kernel: [  196.835829] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:25:59 ryan-ThinkPad-X230 kernel: [  196.849554] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:25:59 ryan-ThinkPad-X230 kernel: [  197.049597] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:25:59 ryan-ThinkPad-X230 kernel: [  197.253067] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:25:59 ryan-ThinkPad-X230 kernel: [  197.456520] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:26:08 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:e9:be:00 (SSID='bulldogs' freq=2437 MHz)
Sep 18 12:26:08 ryan-ThinkPad-X230 kernel: [  205.619996] wlan0: authenticate with 00:0b:86:e9:be:00
Sep 18 12:26:08 ryan-ThinkPad-X230 kernel: [  205.674173] wlan0: send auth to 00:0b:86:e9:be:00 (try 1/3)
Sep 18 12:26:08 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to associate with 00:0b:86:e9:be:00 (SSID='bulldogs' freq=2437 MHz)
Sep 18 12:26:08 ryan-ThinkPad-X230 kernel: [  205.676745] wlan0: authenticated
Sep 18 12:26:08 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 18 12:26:08 ryan-ThinkPad-X230 kernel: [  205.679453] wlan0: associate with 00:0b:86:e9:be:00 (try 1/3)
Sep 18 12:26:08 ryan-ThinkPad-X230 kernel: [  205.684038] wlan0: RX AssocResp from 00:0b:86:e9:be:00 (capab=0x421 status=0 aid=2)
Sep 18 12:26:08 ryan-ThinkPad-X230 kernel: [  205.684041] wlan0: associated
Sep 18 12:26:08 ryan-ThinkPad-X230 wpa_supplicant[1279]: Associated with 00:0b:86:e9:be:00
Sep 18 12:26:08 ryan-ThinkPad-X230 wpa_supplicant[1279]: CTRL-EVENT-CONNECTED - Connection to 00:0b:86:e9:be:00 completed (reauth) [id=0 id_str=]
Sep 18 12:26:08 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: associating -> completed
Sep 18 12:27:20 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:27:20 ryan-ThinkPad-X230 kernel: [  277.439105] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:27:20 ryan-ThinkPad-X230 kernel: [  277.483173] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:27:20 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 18 12:27:20 ryan-ThinkPad-X230 kernel: [  277.682797] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:27:20 ryan-ThinkPad-X230 kernel: [  277.886269] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:27:20 ryan-ThinkPad-X230 kernel: [  278.089760] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:27:28 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:27:28 ryan-ThinkPad-X230 kernel: [  286.206736] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:27:28 ryan-ThinkPad-X230 kernel: [  286.218449] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:27:29 ryan-ThinkPad-X230 kernel: [  286.420389] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:27:29 ryan-ThinkPad-X230 kernel: [  286.623864] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:27:29 ryan-ThinkPad-X230 kernel: [  286.827342] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:27:37 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:27:37 ryan-ThinkPad-X230 kernel: [  294.888858] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:27:37 ryan-ThinkPad-X230 kernel: [  294.892199] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:27:37 ryan-ThinkPad-X230 kernel: [  295.094112] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:27:38 ryan-ThinkPad-X230 kernel: [  295.297617] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:27:38 ryan-ThinkPad-X230 kernel: [  295.501106] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:27:46 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:27:46 ryan-ThinkPad-X230 kernel: [  303.570580] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:27:46 ryan-ThinkPad-X230 kernel: [  303.573899] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:27:46 ryan-ThinkPad-X230 kernel: [  303.775883] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:27:46 ryan-ThinkPad-X230 kernel: [  303.979356] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:27:46 ryan-ThinkPad-X230 kernel: [  304.182798] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:27:55 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:27:55 ryan-ThinkPad-X230 kernel: [  312.251783] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:27:55 ryan-ThinkPad-X230 kernel: [  312.255461] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:27:55 ryan-ThinkPad-X230 kernel: [  312.457601] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:27:55 ryan-ThinkPad-X230 kernel: [  312.661090] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:27:55 ryan-ThinkPad-X230 kernel: [  312.864530] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:28:03 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:28:03 ryan-ThinkPad-X230 kernel: [  320.996945] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:28:03 ryan-ThinkPad-X230 kernel: [  321.008734] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:28:03 ryan-ThinkPad-X230 kernel: [  321.211155] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:28:04 ryan-ThinkPad-X230 kernel: [  321.414667] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:28:04 ryan-ThinkPad-X230 kernel: [  321.618082] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:28:12 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:28:12 ryan-ThinkPad-X230 kernel: [  329.708692] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:28:12 ryan-ThinkPad-X230 kernel: [  329.719551] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:28:12 ryan-ThinkPad-X230 kernel: [  329.920789] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:28:12 ryan-ThinkPad-X230 kernel: [  330.124308] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:28:13 ryan-ThinkPad-X230 kernel: [  330.327782] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:28:21 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:28:21 ryan-ThinkPad-X230 kernel: [  338.399342] wlan0: authenticate with 00:0b:86:ed:55:f0
Sep 18 12:28:21 ryan-ThinkPad-X230 kernel: [  338.440438] wlan0: send auth to 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:28:21 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to associate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:28:21 ryan-ThinkPad-X230 kernel: [  338.642459] wlan0: send auth to 00:0b:86:ed:55:f0 (try 2/3)
Sep 18 12:28:21 ryan-ThinkPad-X230 kernel: [  338.644427] wlan0: authenticated
Sep 18 12:28:21 ryan-ThinkPad-X230 kernel: [  338.646417] wlan0: associate with 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:28:21 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 18 12:28:21 ryan-ThinkPad-X230 kernel: [  338.649394] wlan0: RX AssocResp from 00:0b:86:ed:55:f0 (capab=0x401 status=0 aid=2)
Sep 18 12:28:21 ryan-ThinkPad-X230 kernel: [  338.649400] wlan0: associated
Sep 18 12:28:21 ryan-ThinkPad-X230 wpa_supplicant[1279]: Associated with 00:0b:86:ed:55:f0
Sep 18 12:28:21 ryan-ThinkPad-X230 wpa_supplicant[1279]: CTRL-EVENT-CONNECTED - Connection to 00:0b:86:ed:55:f0 completed (reauth) [id=0 id_str=]
Sep 18 12:28:21 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: associating -> completed
Sep 18 12:28:53 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:28:53 ryan-ThinkPad-X230 kernel: [  370.845750] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:28:53 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 18 12:28:53 ryan-ThinkPad-X230 kernel: [  370.889756] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:28:53 ryan-ThinkPad-X230 kernel: [  371.091204] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:28:54 ryan-ThinkPad-X230 kernel: [  371.294717] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:28:54 ryan-ThinkPad-X230 kernel: [  371.498194] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:29:02 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:29:02 ryan-ThinkPad-X230 kernel: [  379.561277] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:29:02 ryan-ThinkPad-X230 kernel: [  379.575754] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:29:02 ryan-ThinkPad-X230 kernel: [  379.776928] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:29:02 ryan-ThinkPad-X230 kernel: [  379.980396] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:29:03 ryan-ThinkPad-X230 kernel: [  380.183872] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:29:11 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:29:11 ryan-ThinkPad-X230 kernel: [  388.242783] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:29:11 ryan-ThinkPad-X230 kernel: [  388.255550] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:29:11 ryan-ThinkPad-X230 kernel: [  388.458706] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:29:11 ryan-ThinkPad-X230 kernel: [  388.662165] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:29:11 ryan-ThinkPad-X230 kernel: [  388.865614] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:29:19 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:29:19 ryan-ThinkPad-X230 kernel: [  397.017480] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:29:19 ryan-ThinkPad-X230 kernel: [  397.028322] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:29:20 ryan-ThinkPad-X230 kernel: [  397.228159] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:29:20 ryan-ThinkPad-X230 kernel: [  397.431673] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:29:20 ryan-ThinkPad-X230 kernel: [  397.635152] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:29:28 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:29:28 ryan-ThinkPad-X230 kernel: [  405.810877] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:29:28 ryan-ThinkPad-X230 kernel: [  405.824254] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:29:29 ryan-ThinkPad-X230 kernel: [  406.025630] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:29:29 ryan-ThinkPad-X230 kernel: [  406.229117] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:29:29 ryan-ThinkPad-X230 kernel: [  406.432595] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:29:37 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:29:37 ryan-ThinkPad-X230 kernel: [  414.594753] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:29:37 ryan-ThinkPad-X230 kernel: [  414.607709] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:29:37 ryan-ThinkPad-X230 kernel: [  414.811113] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:29:38 ryan-ThinkPad-X230 kernel: [  415.014555] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:29:38 ryan-ThinkPad-X230 kernel: [  415.218027] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:29:46 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:29:46 ryan-ThinkPad-X230 kernel: [  423.378119] wlan0: authenticate with 00:0b:86:ed:55:f0
Sep 18 12:29:46 ryan-ThinkPad-X230 kernel: [  423.419248] wlan0: send auth to 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:29:46 ryan-ThinkPad-X230 kernel: [  423.620526] wlan0: send auth to 00:0b:86:ed:55:f0 (try 2/3)
Sep 18 12:29:46 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to associate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:29:46 ryan-ThinkPad-X230 kernel: [  423.823986] wlan0: send auth to 00:0b:86:ed:55:f0 (try 3/3)
Sep 18 12:29:46 ryan-ThinkPad-X230 kernel: [  423.825908] wlan0: authenticated
Sep 18 12:29:46 ryan-ThinkPad-X230 kernel: [  423.827950] wlan0: associate with 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:29:46 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 18 12:29:46 ryan-ThinkPad-X230 kernel: [  423.831260] wlan0: RX AssocResp from 00:0b:86:ed:55:f0 (capab=0x401 status=0 aid=2)
Sep 18 12:29:46 ryan-ThinkPad-X230 kernel: [  423.831264] wlan0: associated
Sep 18 12:29:46 ryan-ThinkPad-X230 wpa_supplicant[1279]: Associated with 00:0b:86:ed:55:f0
Sep 18 12:29:46 ryan-ThinkPad-X230 wpa_supplicant[1279]: CTRL-EVENT-CONNECTED - Connection to 00:0b:86:ed:55:f0 completed (reauth) [id=0 id_str=]
Sep 18 12:29:46 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: associating -> completed
Sep 18 12:30:53 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:30:53 ryan-ThinkPad-X230 kernel: [  490.261324] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:30:53 ryan-ThinkPad-X230 kernel: [  490.305350] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:30:53 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 18 12:30:53 ryan-ThinkPad-X230 kernel: [  490.504937] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:30:53 ryan-ThinkPad-X230 kernel: [  490.708459] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:30:54 ryan-ThinkPad-X230 kernel: [  490.911933] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:31:02 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:31:02 ryan-ThinkPad-X230 kernel: [  498.960684] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:31:02 ryan-ThinkPad-X230 kernel: [  498.974289] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:31:02 ryan-ThinkPad-X230 kernel: [  499.174734] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:31:02 ryan-ThinkPad-X230 kernel: [  499.378180] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:31:02 ryan-ThinkPad-X230 kernel: [  499.581661] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:31:10 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:31:10 ryan-ThinkPad-X230 kernel: [  507.744656] wlan0: authenticate with 00:0b:86:ed:55:f0
Sep 18 12:31:11 ryan-ThinkPad-X230 kernel: [  507.778678] wlan0: send auth to 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:31:11 ryan-ThinkPad-X230 kernel: [  507.980119] wlan0: send auth to 00:0b:86:ed:55:f0 (try 2/3)
Sep 18 12:31:11 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to associate with 00:0b:86:ed:55:f0 (SSID='bulldogs' freq=5805 MHz)
Sep 18 12:31:11 ryan-ThinkPad-X230 kernel: [  508.183600] wlan0: send auth to 00:0b:86:ed:55:f0 (try 3/3)
Sep 18 12:31:11 ryan-ThinkPad-X230 kernel: [  508.185379] wlan0: authenticated
Sep 18 12:31:11 ryan-ThinkPad-X230 kernel: [  508.187698] wlan0: associate with 00:0b:86:ed:55:f0 (try 1/3)
Sep 18 12:31:11 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 18 12:31:11 ryan-ThinkPad-X230 kernel: [  508.190901] wlan0: RX AssocResp from 00:0b:86:ed:55:f0 (capab=0x401 status=0 aid=2)
Sep 18 12:31:11 ryan-ThinkPad-X230 kernel: [  508.190904] wlan0: associated
Sep 18 12:31:11 ryan-ThinkPad-X230 wpa_supplicant[1279]: Associated with 00:0b:86:ed:55:f0
Sep 18 12:31:11 ryan-ThinkPad-X230 wpa_supplicant[1279]: CTRL-EVENT-CONNECTED - Connection to 00:0b:86:ed:55:f0 completed (reauth) [id=0 id_str=]
Sep 18 12:31:11 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: associating -> completed
Sep 18 12:32:53 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:32:53 ryan-ThinkPad-X230 kernel: [  609.949219] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:32:53 ryan-ThinkPad-X230 NetworkManager[941]: <info> (wlan0): supplicant interface state: completed -> authenticating
Sep 18 12:32:53 ryan-ThinkPad-X230 kernel: [  609.993200] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:32:53 ryan-ThinkPad-X230 kernel: [  610.193975] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:32:53 ryan-ThinkPad-X230 kernel: [  610.397491] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:32:54 ryan-ThinkPad-X230 kernel: [  610.601055] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:33:02 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:33:02 ryan-ThinkPad-X230 kernel: [  618.666805] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:33:02 ryan-ThinkPad-X230 kernel: [  618.681134] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:33:02 ryan-ThinkPad-X230 kernel: [  618.883696] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 2/3)
Sep 18 12:33:02 ryan-ThinkPad-X230 kernel: [  619.087191] wlan0: direct probe to 00:0b:86:ed:55:e0 (try 3/3)
Sep 18 12:33:02 ryan-ThinkPad-X230 kernel: [  619.290677] wlan0: authentication with 00:0b:86:ed:55:e0 timed out
Sep 18 12:33:11 ryan-ThinkPad-X230 wpa_supplicant[1279]: Trying to authenticate with 00:0b:86:ed:55:e0 (SSID='bulldogs' freq=2462 MHz)
Sep 18 12:33:11 ryan-ThinkPad-X230 kernel: [  627.450792] wlan0: authenticate with 00:0b:86:ed:55:e0
Sep 18 12:33:11 ryan-ThinkPad-X230 kernel: [  627.464693] wlan0: send auth to 00:0b:86:ed:55:e0 (try 1/3)
Sep 18 12:33:11 ryan-ThinkPad-X230 kernel: [  627.470671] wlan0: 00:0b:86:ed:55:e0 denied authentication (status 17)

---

### Post by rfporto on 2012-09-18
That was while disconnected

---

### Post by rfporto on 2012-09-20
Okay Chili, I have posted the results I got from using my comp at school, the first while connected to the internet, the second as I was dropped.

---

### Post by chili555 on 2012-09-20
> <info> (wlan0): roamed from BSSID 00:0B:86:ED:88:[COLOR="Red"]**70**[/COLOR] (bulldogs) to 00:0B:86:ED:55:[COLOR="Red"]**F0**[/COLOR] (bulldogs)So we see the same issue; roaming among identically named but different SSIDs. I expect your cofiguration holds the encryption key for one but not the other and so you get dropped. We need to find a way to stop roaming, just like my ex-girlfriend.

rfporto, are you still on Network Manager or did you install Wicd and, ideally, remove NM? I'll attempt to find a solution either way, I just need to know which you have.

---

### Post by rfporto on 2012-09-20
I currently have network manager, but I am willing to install wicd if you prefer it.  Just let me know the steps if that is what you need.  I really know nothing about linux, and am in the process of learning.  Again thank you so much for your help.  Also, I tried to edit the network from infrastructure to AD-hoc and disable the 5ghz band, but this did not fix the problem.

---

### Post by chili555 on 2012-09-21
Let's stick with NM until it proves to us it can't do the job. I assume this is the network you want:> <info> (wlan0): roamed from [COLOR="Red"]BSSID 00:0B:86:ED:88:70 (bulldogs)[/COLOR] to 00:0B:86:ED:55:F0 (bulldogs) Please edit Network Manager and fill in the BSSID in the appropriate box in the same format: 00:0B:86:ED:88:70. <--Those are zeros; *not* the letter O for orange. Please see attached. Also check 'Connect automatically.' Save and close and tell us if the issue is fixed, better, worse or if you sledgehammered the laptop...just kidding.

---

### Post by Earsplit on 2012-09-22
Thanks for all your help Chili. +mad props and kudos. However after battling this for weeks I finally found a fix that worked for me:

Switching to arch linux.

Once the mainstream kernel updates to more recent drivers, I'm sure this will get sorted out. I've had no dropouts or connection issues the last week, running full speed wireless N.

Good luck to all else who encounter this bug.

---

### Post by plaut on 2012-09-27
> **chili555 said:**
> Please edit Network Manager and fill in the BSSID in the appropriate box in the same format

I've been having the same problems - WPA2 authentication works in a mixed G/N network with common ESSID, but when (for some unknown reason) the system roams from N to G, the connection drops (and, unlike Earsplit, I'd prefer not to run Arch linux).  Just wanted to say that your suggestion of setting the BSSID explicitly (to the value from the initial successful authentication) solved the problem for me (and to say thanks!).

---

### Post by zzebu on 2012-10-04
> **chili555 said:**
> Let's stick with NM until it proves to us it can't do the job. I assume this is the network you want:Please edit Network Manager and fill in the BSSID in the appropriate box in the same format: 00:0B:86:ED:88:70. <--Those are zeros; *not* the letter O for orange. Please see attached. Also check 'Connect automatically.' Save and close and tell us if the issue is fixed, better, worse or if you sledgehammered the laptop...just kidding.
Thank you ! I've been having this issue for months, and it seems as though the issue is resolved through this configuration.

---

### Post by lunatico on 2012-11-16
> **chili555 said:**
> Let's stick with NM until it proves to us it can't do the job. I assume this is the network you want:Please edit Network Manager and fill in the BSSID in the appropriate box in the same format: 00:0B:86:ED:88:70. <--Those are zeros; *not* the letter O for orange. Please see attached. Also check 'Connect automatically.' Save and close and tell us if the issue is fixed, better, worse or if you sledgehammered the laptop...just kidding.

Hi!

I have this same wireless card and I also get this problem on WPA2 Enterprise PEAP network. I've had this for years now, I do think it's NM.

You suggestion here looks promising. I'll give it a shot.

What I did was "iwlist wlan0 scan" and searched for the desired ESSID with highest signal (the one closest to Quality=70/70).

I then took that MAC and entered it on NM settings for BSSID as you describe.

When I reboot it connects fine. But if I go to another location on the building, where the AP is different, and reboot, then it won't connect.

So what I see so far is that for this solution to work I have to be at my desk, where the AP I configured is. Right?

Now what will happen when I start moving around? Will it roam? I haven't tried. If it doesn't my next thought is to gather the MAC addresses of all APs on the building (there must be like 10) and configure on wireless connection for each. Not sure if this would work.

We'll see! I'll keep posting with updates.

---

### Post by chili555 on 2012-11-16
> So what I see so far is that for this solution to work I have to be at my desk, where the AP I configured is. Right?Yes.> Now what will happen when I start moving around? Will it roam?No, or at least that's the intent: to *keep* it from roaming.

Network Manager is still an imperfect being. Multiple ESSIDs with the exact same name are still troublesome.

---

### Post by plaut on 2012-11-16
> **lunatico said:**
> ...gather the MAC addresses of all APs on the building (there must be like 10) and configure on wireless connection for each.

This is what I've been doing - creating specific variants of the original connection with a unique name and BSSID for each location.  NM then automatically connects to the strongest one - clumsy but it works.

---

### Post by lunatico on 2012-11-30
> **plaut said:**
> This is what I've been doing - creating specific variants of the original connection with a unique name and BSSID for each location.  NM then automatically connects to the strongest one - clumsy but it works.

I tried this and didn't work for me. Maybe because all AP are for the same ESSID?

---

### Post by plaut on 2012-11-30
> **lunatico said:**
> I tried this and didn't work for me. Maybe because all AP are for the same ESSID?

The ESSID shouldn't matter (it's the same across all of the APs I'm connecting to).  Are you sure you're setting the BSSID to the *first* AP you connect to? Do things work when you're connected to it (but not after you roam to another one)?  If not, you might have a different problem....

---

### Post by lunatico on 2012-11-30
> **plaut said:**
> The ESSID shouldn't matter (it's the same across all of the APs I'm connecting to).  Are you sure you're setting the BSSID to the *first* AP you connect to? Do things work when you're connected to it (but not after you roam to another one)?  If not, you might have a different problem....

Yes, so I configured the BSSID to be the one which succeeded in the authentication. But then when moving around and once it's connected it's all good. But when I move to another location, even if I have saves another BSSID for that location, it does not reconnect. I pretty much does the same, it will loose connectivity, eventually NM tries to reconnect and brings up the password dialogbox, if I click connect it won't connect, if I click cancel it'll try to reconnect but will never succeed. I'll have to turn off wireless and turn it back on, then select the strongest signal and connect.

---

### Post by plaut on 2012-11-30
I haven't tried moving from one BSSID-specific connection to another - what you describe may be as good as it gets at this point....

---

### Post by lunatico on 2012-11-30
Yeah... if I don't move location it's rock solid. The problem is when I move location. I think maybe if I turn off wireless, move location then turn on again it might connect fine and solid. Will try next week.

---

### Post by lunatico on 2012-12-06
Sad. This is so annoying. It looks like I'm forced to ditch network manager and install WICD.

---

### Post by Autumn Corvus on 2012-12-09
I have the same wifi card in a Thinkpad T430 and it's given me all sorts of trouble.

---

