---
title: "D-link - airmon-ng problem DWL-G650"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by ryanfx on 2008-12-18
Hey guys - I have an atheros based card (DWL-G650) and I am trying to run airodump-ng based off on the interface created by airmon-ng

It brings up an interface in monitor mode but when I run:

airodump-ng ath1

the screen never shows any wireless activity at all even though the Ubuntu wireless Networks clearly shows there are a few - any ideas??

```

ryan@UbuntuLaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:9646  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by ryanfx on 2008-12-18
bump

---

