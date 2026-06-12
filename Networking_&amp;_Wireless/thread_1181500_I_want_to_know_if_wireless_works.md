---
title: "I want to know if wireless works"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by Richmoar on 2009-06-08
Hey all,

I'm trying to figure out if my wireless card works at all under ubuntu 9.04, but I just can't tell because on its own it does not detect open networks.

I typed a command not knowing much of what it displays: iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID: off/any  
          Mode:Managed  Channel: 0  Access Point: Not-Associated   
          Bit Rate: 0 kb/s   Tx-Power= off   Sensitivity= 8/0  
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

eth3      no wireless extensions.

IS my wireless working? And if it is how can I connect to the network im wired to wirelessly?

---

### Post by superprash2003 on 2009-06-08
post output of the following
1)sudo iwlist scanning
2)lshw -C network

---

