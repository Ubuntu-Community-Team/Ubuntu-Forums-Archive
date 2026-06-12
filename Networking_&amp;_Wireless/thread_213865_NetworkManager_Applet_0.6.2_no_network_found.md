---
title: "NetworkManager Applet 0.6.2 no network found"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by orb9220 on 2006-07-11
But I'm and connected fine.

It is the NetworkManager Applet 0.6.2 in the about box also know as the
nm-applet.

I have had this problem before and can't remember if I did something or it did something.

It is showing a red circle no networks found.

Is there a file I am to edit?

 iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11g  ESSID:"www.personaltelco.net"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:06:25:D8:9A:F3
          Bit Rate:5 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/94  Signal level=-75 dBm  Noise level=-95 dBm
          Rx invalid nwid:109  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:47  Invalid misc:47   Missed beacon:0

sit0      no wireless extensions.

---

### Post by orb9220 on 2006-07-11
Found the ant ser

Thanks to nonotube!

"f it is not managing your network connections after upgrading to Dapper, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let NetworkManager handle them.
"

](*,)

---

