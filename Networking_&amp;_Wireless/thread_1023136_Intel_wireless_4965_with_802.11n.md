---
title: "Intel wireless 4965 with 802.11n"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by fergus on 2008-12-27
Hello, 

I am trying to configure my lenovo T61 with intel 4965 wireless running intrepid to a dlink DAP-1522 using 802.11n.  I am using the dlink in an access point mode and configured it to only accept 802.11n connections in the 5GHz band.  Using network manager, I was able to connect but the reported speed by iwconfig is only 54Mb/s.  I have tried to force a higher bit rate with iwconfig without success.  Everything appears to work, I have a good signal, the connection works, its just slower than anticipated.  In comparison, using Vista I can achieve 90Mb/s.  Anybody able to get iwconfig to report a higher bit rate than 54Mb/s?  Any ideas on what could be the problem? Thanks for the help.

I am also using the backported kernel modules to avoid the kernel panic issue.

fergus

iwconfig output:

wlan0     IEEE 802.11abgn  ESSID:"mynetwork"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 00:22:B0:60:A0:CB   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=55/100  Signal level:-69 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by xoon on 2008-12-29
I have the same problem, under Vista 130Mb/s. File tranfer under Linux 2.5 MB/s under Vista 6/7 MB/s

---

