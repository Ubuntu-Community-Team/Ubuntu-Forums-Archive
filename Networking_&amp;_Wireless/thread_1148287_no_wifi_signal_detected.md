---
title: "no wifi signal detected"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by adambh on 2009-05-04
The wifi connects to the network (which has a strong signal because my laptop connects easily)



adam@adamdesk:~$ iwconfig wlan0

wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 7E:B5:10:6B:21:57   
          Tx-Power=12 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

adam@adamdesk:~$ lsmod | grep rt73
rt73                  244876  0 
rt73usb                33412  0 
crc_itu_t              10112  1 rt73usb
rt2x00usb              18688  1 rt73usb
rt2x00lib              37888  2 rt73usb,rt2x00usb
adam@adamdesk:~$ uname -a
Linux adamdesk 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
adam@adamdesk:

---

