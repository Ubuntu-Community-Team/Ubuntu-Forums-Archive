---
title: "Atheros AR5413/5414 - Ubuntu 12.04 - Versalogic_Cobra_EBX-12 embedded computer"
date: 2012-08-07
forum: Networking &amp; Wireless
---

### Post by adriantoravi on 2012-08-07
Hello, recently I installed ubuntu 12.04 server, and I can't
get wireless working. Following the sticky "How to post wireless
issue", this is the commands and their outputs:
```
lspci -nnk | grep -iA2 net
```
```
02:03.0 Ethernet controller [0200]: Atheros Communications Inc. AR5413/AR5414 Wireless Network Adapter [AR5006X(S) 802.11abg] [168c:001b] (rev 01)
	Subsystem: Atheros Communications Inc. EnGenius EMP-8602 (400mw) or Compex WLM54AG [168c:2063]
	Kernel driver in use: ath5k
--
02:05.0 Ethernet controller [0200]: Intel Corporation 8255xER/82551IT Fast Ethernet Controller [8086:1209] (rev 10)
	Kernel driver in use: e100
	Kernel modules: e100
```

```
iwconfig
```
```
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

```
rfkill list all
```
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
lsmod | grep "ath5k"
```
```
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
```

```
dmesg | grep "ath5k"
```
```
[    7.344518] ath5k 0000:02:03.0: registered as 'phy0'
[    8.205123] ath5k phy0: Atheros AR5413 chip found (MAC: 0xa4, PHY: 0x61)
```

Thank you

---

