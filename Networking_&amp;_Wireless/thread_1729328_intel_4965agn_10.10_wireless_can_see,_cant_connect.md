---
title: "intel 4965agn 10.10 wireless can see, cant connect"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by nomand on 2011-04-14
Hi, gonna be my first post here, I'm trying to set up ubuntu on my netbook, the brand and make is obscure, essentially, this is a no-name brandless build from china, but a pretty decent lappy. Atom N270 Intel 945GSE based.

initially it was equipped with a 3DSP wifi/bluetooth mPCIe combo card, which is proprietary and didn't work on ubuntu (didn't even show up as a device), so I got an intel 4965agn based on compatibility list somewhere in the wiki.

The problem I have is that I see networks, but can't connect at home or at work or anywhere, it just hangs in the connecting status and then throws the authentication popup at me again (pw is all correct). I tried looking around at similar problems, some have wpa_supplicant related issues, but doesn't seem to be the same as mine.

I tried creating an unsecured network using my macbook's airport, and same thing happened with ubuntu... hangs in connecting status then drops, so it doesn't seem to be WPA.

I don't have the device on me to do all the iflist iwlist checks for you, but if you could give me some clues, I'll post back when I get home.

Thanks!

---

### Post by nomand on 2011-04-15
[COLOR=#000000][FONT=Arial]just ran some tests,[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I'm  able to connect to my macbook if I create a network from there, I am  also able to connect to the ubuntu machine with my macbook, however i  made a WEP protected network using the macbook and it can't connect.  Trying to connect to my router the "wireless authentication required"  window pops up again as well and doesn't connect.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Seems to me the wireless is having trouble saving the access key or some kind of wireless security issue with the driver.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]some  people with connectivity issues point to the N network functionality,  but I dont think this is the same case, as I tested before, being able  to connect to an unsecured network.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]**lspci -v | less**[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Subsystem: Intel Corporation Vaio VGN-SZ79SN_C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Physical Slot: 33[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Flags: bus master, fast devsel, latency 0, IRQ 45[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Memory at feafe000 (64-bit, non-prefetchable) [size=8K][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Kernel driver in use: iwlagn[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Kernel modules: iwlagn[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]**iwconfig**[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]lo[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]no wireless extensions.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]no wireless extensions.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IEEE 802.11abg ESSID:off/any[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]mode:Ad-Hoc Frequency:2.412 GHz Cell: Not-Associated[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Tx-Power=14 dBm[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Retry long limit:7 RTS thr:off Fragment thr:off[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Power Management: off[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]**lsmod | grep iwlagn**[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]iwlagn                333500  0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iwlcore               167503  1 iwlagn[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]mac80211              294370  2 iwlagn,iwlcore[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]cfg80211              178528  3 iwlagn,iwlcore,mac80211[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]**dmesg | grep iwl**[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial][   14.250441] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][   14.250449] iwlagn: Copyright(c) 2003-2010 Intel Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][   14.250569] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][   14.250583] iwlagn 0000:02:00.0: setting latency timer to 64[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][   14.250633] iwlagn 0000:02:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][   14.289562] iwlagn 0000:02:00.0: device EEPROM VER=0x36, CALIB=0x5[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][   14.296578] iwlagn 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][   14.296692] iwlagn 0000:02:00.0: irq 45 for MSI/MSI-X[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][   14.588123] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][   15.027492] phy0: Selected rate control algorithm 'iwl-agn-rs'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][  118.820182] iwlagn 0000:02:00.0: failed to remove IBSS station 00:00:00:00:00:00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][  125.924315] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][  125.928639] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][  653.651760] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][  653.656026] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][  935.830796] iwlagn 0000:02:00.0: failed to remove IBSS station 00:00:00:00:00:00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][ 1433.027748] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][ 1433.032091] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]**ls /etc/modprobe.d**[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]alsa-base.conf              blacklist-modem.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]blacklist-ath_pci.conf      blacklist-oss.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]blacklist.conf              blacklist-watchdog.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]blacklist-firewire.conf     intel-5300-iwlagn-disable11n.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]blacklist-framebuffer.conf[/FONT][/COLOR]

```

---

