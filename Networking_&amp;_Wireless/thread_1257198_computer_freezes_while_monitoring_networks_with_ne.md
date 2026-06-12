---
title: "computer freezes while monitoring networks with new wireless card"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by bike756 on 2009-09-03
I recently purchased a stronger wireless card of the sort that plug into a USB and made a nice little dish for it to enhance the signal to *cough* better test my own security *cough*. 

I am trying to crack the WEP encryption of several networks using aircrack-ng and the associated airmon, airodump, etc. I have done plenty of WEP cracking with the wireless card in my laptop, so I am not inexperienced, however, I am having trouble getting it to work with the new card. When I put the card in monitor mode using 

sudo airmon-ng start ra0

the computer completely freezes. The first time I tried this, it worked, after that though, it froze once I started airodump.

Here is the result of iwconfig:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"wangpg"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:D1:43:2F:7C   
          Bit Rate=18 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=55/100  Signal level:-82 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"wangpg"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:92:FE:5B   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=51/100  Signal level:-78 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

wlan0 is the one I used successfully before. ra0 is the new one. 

Any suggestions greatly appreciated :)

---

### Post by bike756 on 2009-09-04
Anyone?

---

