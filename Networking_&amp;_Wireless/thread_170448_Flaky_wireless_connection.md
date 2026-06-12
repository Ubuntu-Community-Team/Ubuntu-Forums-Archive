---
title: "Flaky wireless connection"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by sveinn on 2006-05-04
Hello, 

I am running 5.10 on Dell Inspiron 6000 and have the following problem (only on Ubuntu, not when I boot XP).

Frequently (up to 10 times a day), the wireless connection "flakes out", ie becomes disconnected. 

iwconfig reveals the following informationf or my wireless connection (eth1)

eth1      unassociated  ESSID:"PrGdns"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:09:5B:CB:55:F6 

          Bit Rate=36 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

(Notice that it says "unassociated" compared with "IEEE 802.11g" when connected)

iwlist scan returns

eth1      No scan results

I've tried juggling with various settings (Network settings panel, iwconfig, etc), but I it seems the connection spontaneously comes back on after a little while - 30 seconds to several minutes. 

Again - I have NOT experienced this problem in Windows XP, so I do not think it is a hardware problem. 

Any clues?

Thanks, 

Sveinn 

PS The network controller is Intel Pro/Wireless (as per lspci):

0000:03:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

- added 11.05.2006 -

see also 

[http://www.ubuntuforums.org/showthread.php?t=136673](http://www.ubuntuforums.org/showthread.php?t=136673)

---

