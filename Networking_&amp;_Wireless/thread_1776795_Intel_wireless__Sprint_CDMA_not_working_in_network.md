---
title: "Intel wireless / Sprint CDMA not working in network manager 11.04 on Latitude E4310"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by soulmata on 2011-06-06
Hello,

Since an upgrade from 10.10 to 11.04, all wireless devices for me in the plasma network manager applet are not functioning properly on a Dell Latitude E4310

Specific problem: No wireless networks appear in the plasma network manager applet. Manually-configured networks do not connect. A separate CDMA card appears, but cannot establish a connection. The CDMA card does function on 10.10 machines, and formerly worked on this machine.

The only wireless 'network' that appears in the plasma network manager widget is 'hidden network'. Manually adding a network and checking "Connect Automatically" does nothing. I attempted a fresh install after the upgrade itself failed the work. There are no networks to click on, and selecting the device itself merely shows the status page.

Further information

iwconfig output:
```
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

rfkill output:
```

0: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: dell-wwan: Wireless WAN
        Soft blocked: no
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

dmesg output:
```
dmesg | grep iwl
[   24.292605] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   24.292610] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   24.292687] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.292696] iwlagn 0000:02:00.0: setting latency timer to 64
[   24.292744] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   24.302475] iwlagn 0000:02:00.0: device EEPROM VER=0x436, CALIB=0x6
[   24.302480] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   24.302481] iwlagn 0000:02:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   24.302510] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   24.302599] iwlagn 0000:02:00.0: irq 44 for MSI/MSI-X
[   24.316555] iwlagn 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   24.320865] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[13171.290238] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.
[13171.462882] iwlagn 0000:02:00.0: Not sending command - RF KILL
[13171.462890] iwlagn 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[13171.462896] iwlagn 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-5)
[13185.853564] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.
[13868.995233] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.
[13869.087256] iwlagn 0000:02:00.0: Not sending command - RF KILL
[13869.087262] iwlagn 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[13869.087267] iwlagn 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-5)
[13885.439975] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.

```

dmesg output again:
```
dmesg | grep cfg802
[   24.029001] cfg80211: Calling CRDA to update world regulatory domain
[   24.125605] cfg80211: World regulatory domain updated:
[   24.125609] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.125612] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.125614] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.125617] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.125620] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.125622] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.316828] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   25.135045] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   27.240007] cfg80211: Found new beacon on frequency: 5745 MHz (Ch 149) on phy0
[   27.283905] cfg80211: Found new beacon on frequency: 5765 MHz (Ch 153) on phy0
[   27.565129] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[14569.040109] cfg80211: Found new beacon on frequency: 5805 MHz (Ch 161) on phy0

```

dmesg output again:
```
dmesg | grep -i wlan
[   24.640672] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13186.926252] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13212.802642] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13307.324243] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13416.690887] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13886.546504] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```


Here's the CDMA-specific dmesg output:
```

[17846.948253] usb 2-1.1: new full speed USB device using ehci_hcd and address 7
[17847.060342] sierra 2-1.1:1.0: Sierra USB modem converter detected
[17847.060650] usb 2-1.1: Sierra USB modem converter now attached to ttyUSB1
[17847.060765] usb 2-1.1: Sierra USB modem converter now attached to ttyUSB2
[17847.060838] usb 2-1.1: Sierra USB modem converter now attached to ttyUSB3

```



Neither the CDMA card nor any wireless networks are working. If I take the exact same machine and boot from a disk with 10.10, both work. 

Any ideas?

---

### Post by soulmata on 2011-06-06
Here's an image of the plasma nm applet, showing no networks. (Attached to this post)

Note: If you select "Manage Connections" and use the scan feature in wifi, you do indeed see many wireless networks. Adding them manually to the list does not expose them in the applet or allow you to use them.

---

### Post by soulmata on 2011-06-10
I have not been able to find a solution for this. Any suggestions?

---

