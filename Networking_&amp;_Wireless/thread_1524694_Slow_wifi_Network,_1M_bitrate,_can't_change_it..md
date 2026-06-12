---
title: "Slow wifi Network, 1M bitrate, can't change it."
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by Yuzem on 2010-07-05
I have 1 router 2 pcs. We had to move one pc away from the router so I bought a wifi card.
Everything went fine, the card works and I have internet but the network is incredible slow.

I am using Ubuntu Lucid Lynx 10.04

lspci | grep Wire
```
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

sudo iwconfig wlan0
```
wlan0     IEEE 802.11bg  ESSID:"wert"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:E7:55:1C:3A   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=18/100  Signal level=18/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Then:
```
sudo iwconfig wlan0 rate 54M auto
```
But there are no changes.
Thanks in advance!

---

### Post by Yuzem on 2010-07-06
Ok, I installed ndiswrapper with windows 98 drivers and the bit rate went to 24M then I tried windows 2000 drivers and now I have 54M but the speed is still too slow.
Signal has full strength but when moving a file over the Network the max speed is ~300KB/seg.

Is Wifi 54M supposed to be this slow?

---

### Post by jacquesdupontd on 2011-09-28
When applying such criteria you have to take your card Down before with ifconfig so :

sudo ifconfig wlan0 down
sudo iwconfig wlan0 rate 54M
sudo ifconfig wlan0 up

iwconfig and you'll see the change applied .

Cheers mate.

---

