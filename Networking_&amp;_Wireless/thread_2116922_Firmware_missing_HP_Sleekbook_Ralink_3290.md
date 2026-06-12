---
title: "Firmware missing HP Sleekbook Ralink 3290"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by Suncoaster on 2013-02-17
I have a HP Sleekbook with a Ralink 3290 wireless card.  I had been unable to get this card recognised at all until I installed the 3.7.6 kernel, now I get a wireless option in network manager but with a message "Missing Firmware".  Can anyone help me with this please.  e.g. where can I get this firmware and then how do I install same.

Any and all help would be appreciated.

Output from terminal below

david@HP ~ $ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
david@HP ~ $ iwconfig
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

lo        no wireless extensions.

---

