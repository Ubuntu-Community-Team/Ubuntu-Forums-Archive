---
title: "Intel 5100 AGN - what's my speed?"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by SanchoActual on 2010-04-17
Hoping there's a simple answer to this question, cuz I can't google no more ;-)

My HP dv7 has an Intel 5100 AGN. Karmic (2.6.31-20-generic) found it, enabled it and is loading the correct firmware

```

ls /lib/firmware/*.ucode
/lib/firmware/iwlwifi-1000-3.ucode  /lib/firmware/iwlwifi-5000-1.ucode
/lib/firmware/iwlwifi-3945-1.ucode  /lib/firmware/iwlwifi-5000-2.ucode
/lib/firmware/iwlwifi-3945-2.ucode  /lib/firmware/iwlwifi-5150-2.ucode
/lib/firmware/iwlwifi-4965-1.ucode  /lib/firmware/iwlwifi-6000-4.ucode
/lib/firmware/iwlwifi-4965-2.ucode
===========================================================
dmesg | grep firmware
[   23.030462] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   23.077715] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
```
Speed seems fine (yes, that's quite subjective; haven't done any hard measurements on intraLAN file transfers; still just getting into Ubuntu), and my router (Trendnet TEW-633GR running fixed on chan 2 and g/n) reports the following for this adapter right now:
```
MAC Address	IP Address    Mode	Rate	Signal (%)
00215D148850	0.0.0.0	      11ng	216	96
```
I reckon I can trust it to determine at what speeds devices are connecting.

[SIZE="3"]**[COLOR="Navy"]My question is, is there a way to see this info in Ubuntu?[/COLOR]**[/SIZE]

```
iwconfig

wlan0     IEEE 802.11abgn  ESSID:"Porcupine"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:14:D1:C3:66:D0   
          Bit Rate=0 kb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I promise the "Bit Rate" isn't 0 kb/s ;-)


Some more info:
```
dmesg | grep iw
[   22.870683] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   22.870685] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   22.870771] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.870807] iwlagn 0000:02:00.0: setting latency timer to 64
[   22.870874] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   22.912182] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   22.912264] iwlagn 0000:02:00.0: irq 33 for MSI/MSI-X
[   22.920350] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   23.030462] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   23.077715] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[   23.364549] Registered led device: iwl-phy0::radio
[   23.364569] Registered led device: iwl-phy0::assoc
[   23.364585] Registered led device: iwl-phy0::RX
[   23.364600] Registered led device: iwl-phy0::TX
[   48.707793] iwlagn 0000:02:00.0: iwl_tx_agg_start on ra = 00:14:d1:c3:66:d0 tid = 0
[  957.788594] iwlagn 0000:02:00.0: iwl_tx_agg_start on ra = 00:14:d1:c3:66:d0 tid = 6
[ 2052.289450] iwlagn 0000:02:00.0: iwl_tx_agg_start on ra = 00:14:d1:c3:66:d0 tid = 1
```
These are interesting:
```

[   22.912182] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   22.920350] phy0: Selected rate control algorithm 'iwl-agn-rs'
```
Is N not tunable? What is "tunable"? Guessing the "rate control algorithm" isn't an issue, but since I'm talking about rates....

ANYway, any useful input or even a straight-forward answer (yes, we can dream :-) will be greatly appreciated.

This isn't a complaint. I'm thoroughly stoked that Ubuntu installed so easily and recognized everything without pulling teeth. I'd just love to be able to see my connection speed is all (without logging into my router).

TIA.
Sancho

---

