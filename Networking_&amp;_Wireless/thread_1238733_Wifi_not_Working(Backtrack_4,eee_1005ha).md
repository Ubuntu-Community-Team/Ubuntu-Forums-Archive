---
title: "Wifi not Working(Backtrack 4,eee 1005ha)"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by a94060 on 2009-08-12
Hello Everyone, I have an eee pc 1005ha with an atheros wireless card. I run wicd and am able to see my network. I type in the correct wep key, and wicd associates my card and tells me I am connected. However, I am unable to do any internet related tasks. Here is the typical requested output(after reading the sticky):

dmesg
> wlan0 (ath9k): not using net_device_ops yet
wlan0: direct probe to AP 00:1d:7e:40:0d:b0 try 1
wlan0: direct probe to AP 00:1d:7e:40:0d:b0 try 1
wlan0: direct probe to AP 00:1d:7e:40:0d:b0 try 2
wlan0: direct probe to AP 00:1d:7e:40:0d:b0 try 3
wlan0 direct probe responded
wlan0: authenticate with AP 00:1d:7e:40:0d:b0
wlan0: authenticated
wlan0: associate with AP 00:1d:7e:40:0d:b0
wlan0: RX AssocResp from 00:1d:7e:40:0d:b0 (capab=0x411 status=0 aid=1)
wlan0: associated
wlan0: deauthenticating by local choice (reason=3)
wlan0: deauthenticating by local choice (reason=3)
wlan0: deauthenticating by local choice (reason=3)
wlan0: authenticate with AP 00:1d:7e:40:0d:b0
wlan0: authenticated
wlan0: associate with AP 00:1d:7e:40:0d:b0
wlan0: RX AssocResp from 00:1d:7e:40:0d:b0 (capab=0x411 status=0 aid=1)
wlan0: associated


iwconfig
> wlan0     IEEE 802.11bgn  ESSID:"bungee's network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:40:0D:B0   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=55/100  Signal level:-90 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



lsmod

> ath9k                 300944  0 
mac80211              194492  1 ath9k
led_class               3408  1 ath9k
rfkill                  9328  5 ath9k,eeepc_laptop


lspci
> 01:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


If you need any other information to help me solve my problem, please post back. Thank you very much.

---

### Post by jan0ng on 2009-09-23
I have the same issue here.  I can't activate my wifi

---

### Post by a94060 on 2009-09-23
What you can try to do is try to reinstall the driver. In the end I think I may have damaged it trying to use airsnort/crack. Reinstalling the drivers should fix it.

---

