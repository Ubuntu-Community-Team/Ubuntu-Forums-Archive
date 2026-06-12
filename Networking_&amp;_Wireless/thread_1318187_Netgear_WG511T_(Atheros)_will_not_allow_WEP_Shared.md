---
title: "Netgear WG511T (Atheros) will not allow WEP Shared"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by buzzbob on 2009-11-07
The card work fine if I run without security, and I have to run WEP shared due to other device limitations.  It allows WEP ascii but if I put in my shared key it will not work. 

 lsb_release -d
==============
Description:	Ubuntu 8.04.3 LTS

lspci -nn | grep 'Atheros'
============
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)

iwconfig
============
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

