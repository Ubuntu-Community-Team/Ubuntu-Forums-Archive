---
title: "TP-LINK TL-WN2700ND not working"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by carajillu on 2012-04-29
Hi! I'm a new user in this forum and a less but still new user of Ubuntu. 

I'm running 10.4 and I have a wireless usb TP-LINK TL-WN2700ND that doesn't work in ubuntu but it does in windows xp, so I tried to install the windows driver with ndiswrapper. The driver is correctly installed and the pc somehow "knows" that the usb is there, but it doesn't find any network.

Here is the output of iwconfig:

lo        no wireless extensions.

eth1      no wireless extensions.

wlan3     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
wlan2     IEEE 802.11bg  ESSID:"ORANGE-2ECA84"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:9F:75:CD:93   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The device not working is wlan3 (wlan2 is the one I'm using to write here). I've read that the chipset is Ralink 3070.

Finally, I've found out that the device works with 10.4 in older machines but not in "new" ones.
If you need more information to help me, I'll be glad to post it.

Thanks,
Joan

---

