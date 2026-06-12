---
title: "Slow Wireless on aspire one D260"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by teqmo on 2011-04-03
Where is the settings in the network connections utility for 802.11   **b or g or n?**


AOD260:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Haven"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:BC:8D:13:99   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lspci
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

