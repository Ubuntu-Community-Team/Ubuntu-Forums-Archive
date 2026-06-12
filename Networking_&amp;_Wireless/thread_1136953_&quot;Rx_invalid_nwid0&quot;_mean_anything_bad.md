---
title: "&quot;Rx invalid nwid:0&quot; mean anything bad?"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by eahl4 on 2009-04-25
I get the following response to iwconfig--does "Rx invalid nwid:0" mean anything?:

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"friedline"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:6B:29:9F:86   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=95/100  Signal level:-55 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Thanks in advance!

---

### Post by chili555 on 2009-04-25
> does "Rx invalid nwid:0" mean anything?It means you have not received any packets with an invalid Network ID. This  parameter is only used for pre-802.11 hardware, the 802.11 protocol uses the ESSID and AP Address for this function.

So, it means nothing of any real value.

---

