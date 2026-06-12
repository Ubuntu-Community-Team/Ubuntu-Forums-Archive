---
title: "Thinkpad T520i - Intel 1000 BGN - cannot connect - probes time out"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by mcudrc on 2012-08-27
Hello,

I am having the following issue with my thinkpad and I would be very glad for any help. I cannot connect to any wireless network, the core of this problem is:

```

[ 4555.285545] wlan0: authenticate with d8:5d:4c:f5:53:2a
[ 4555.295346] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 1/3)
[ 4555.498502] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 2/3)
[ 4555.702201] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 3/3)
[ 4555.905869] wlan0: authentication with d8:5d:4c:f5:53:2a timed out
[ 4555.911060] iwlwifi 0000:03:00.0: ACTIVATE a non DRIVER active station id 0 addr d8:5d:4c:f5:53:2a

```

Some more details:
I can scan networks with no problem, I try to connect using wicd. 

I am sure that the AP has no MAC filtering, and that the password is correct. I have tried (with no avail):
 - upgrading from 11.10 to 12.04
 - upgrading the kernel (to 3.4.0)
 - various iwlwifi options - wd_disable=1, 11n_disable=1, swcrypto=1, bt_coex_active=0

Reports and (I hope) relevant stuff:
```

 # uname -a
Linux kolotoc 3.4.0-030400-generic #201205210521 SMP Mon May 21 09:22:02 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

 # cat /etc/issue
Ubuntu 12.04.1 LTS \n \l

 # iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

 # rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
        Soft blocked: no
        Hard blocked: no
5: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

dmesg tail after modprobe -r iwlwifi and modprobe iwlwifi
```

[ 4530.007264] cfg80211: Calling CRDA to update world regulatory domain
[ 4530.013178] cfg80211: World regulatory domain updated:
[ 4530.013182] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4530.013185] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4530.013188] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4530.013191] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4530.013193] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4530.013196] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4530.013717] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 4530.013720] Copyright(c) 2003-2012 Intel Corporation
[ 4530.013862] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[ 4530.013864] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900050a8000
[ 4530.013866] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[ 4530.013995] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[ 4530.018061] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[ 4530.018236] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 4530.018240] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 4530.018242] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 4530.018244] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[ 4530.018246] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[ 4530.018249] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[ 4530.018370] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 4530.037697] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[ 4530.037700] iwlwifi 0000:03:00.0: Device SKU: 0x50
[ 4530.037702] iwlwifi 0000:03:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3
[ 4530.037712] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[ 4530.037844] Registered led device: phy0-led
[ 4530.037876] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 4530.037991] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 4535.013694] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 4535.072212] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 4535.131991] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4535.173532] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 4535.239020] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4535.642173] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 4535.744074] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 4535.744984] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4535.892878] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 4535.993300] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4537.228582] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 4537.228594] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4537.229359] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4544.889420] wlan0: authenticate with d8:5d:4c:f5:53:2a
[ 4544.899257] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 1/3)
[ 4545.101952] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 2/3)
[ 4545.305644] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 3/3)
[ 4545.509351] wlan0: authentication with d8:5d:4c:f5:53:2a timed out
[ 4545.510512] iwlwifi 0000:03:00.0: ACTIVATE a non DRIVER active station id 0 addr d8:5d:4c:f5:53:2a
[ 4555.285545] wlan0: authenticate with d8:5d:4c:f5:53:2a
[ 4555.295346] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 1/3)
[ 4555.498502] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 2/3)
[ 4555.702201] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 3/3)
[ 4555.905869] wlan0: authentication with d8:5d:4c:f5:53:2a timed out
[ 4555.911060] iwlwifi 0000:03:00.0: ACTIVATE a non DRIVER active station id 0 addr d8:5d:4c:f5:53:2a
[ 4565.663858] wlan0: authenticate with d8:5d:4c:f5:53:2a
[ 4565.673829] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 1/3)
[ 4565.875061] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 2/3)
[ 4566.078751] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 3/3)
[ 4566.282447] wlan0: authentication with d8:5d:4c:f5:53:2a timed out
[ 4566.291551] iwlwifi 0000:03:00.0: ACTIVATE a non DRIVER active station id 0 addr d8:5d:4c:f5:53:2a
[ 4573.947855] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 4574.029196] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4574.424576] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 4574.526328] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 4574.526710] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4576.110681] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 4576.110693] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4576.111480] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

Really appreciate any pointers and help,
thx,
Joe

---

### Post by chili555 on 2012-08-27
Hmmm.> - various iwlwifi options - wd_disable=1, 11n_disable=1, swcrypto=1, bt_coex_active=0
From *modinfo*:> parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           *bt_coex_active:enable wifi/bt co-exist (default: enable)* ([COLOR="Red"]bool[/COLOR])
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (default: true) (bool)
I think 'boolean' wants a Y or a N, not an integer. Would you please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi bt_coex_active=N
```Now check *dmesg* and let us know if anything has improved.

---

### Post by mcudrc on 2012-08-31
No, unfortunately, this does not help.
Trying "false", or "disable" raises
```

FATAL: Error inserting iwlwifi (/lib/modules/3.4.10-030410-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko): Invalid argument

```
so I think it would tell if 0 would not be acceptable.


This is the part of dmesg from reloading the module:
```

[70232.110185] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[70232.116227] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[70232.116355] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[70232.116357] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[70232.116359] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[70232.116361] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[70232.116362] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[70232.116365] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[70232.116475] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[70232.135860] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[70232.135863] iwlwifi 0000:03:00.0: Device SKU: 0x50
[70232.135864] iwlwifi 0000:03:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3
[70232.135874] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[70232.136052] Registered led device: phy0-led
[70232.136074] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[70232.136164] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[70249.805778] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[70249.866192] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[70249.930594] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[70261.704424] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[70261.783030] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[70262.325350] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[70262.427144] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[70262.428056] ADDRCONF(NETDEV_UP): eth0: link is not ready
[70262.594132] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[70262.669303] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[70264.119238] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[70264.119244] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[70264.119561] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[70265.184047] wlan0: authenticate with d8:5d:4c:f5:53:2a
[70265.193664] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 1/3)
[70265.394500] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 2/3)
[70265.598234] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 3/3)
[70265.801914] wlan0: authentication with d8:5d:4c:f5:53:2a timed out
[70275.601253] wlan0: authenticate with d8:5d:4c:f5:53:2a
[70275.611139] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 1/3)
[70275.810982] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 2/3)
[70276.014684] wlan0: direct probe to d8:5d:4c:f5:53:2a (try 3/3)
[70276.218419] wlan0: authentication with d8:5d:4c:f5:53:2a timed out

```

Any ideas?
Thank you!

---

### Post by chili555 on 2012-08-31
For kernel 3.2.0-29, the current 12.04 kernel, you might try the compat-wireless package:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic  [COLOR="Red"]<--or -pae[/COLOR]
```For kernel 3.4.xx I have no other suggestions.

---

### Post by mcudrc on 2012-09-21
Hmm, unfortunately, neither bacported module worked.. I have "solved" the problem now, using usb wireless adapter, which worked out-of-box..

Thanks anyway!

---

