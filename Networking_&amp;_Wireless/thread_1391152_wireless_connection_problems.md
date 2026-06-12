---
title: "wireless connection problems"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by Keith Fox on 2010-01-26
I haven't had problems with my wireless network using Ubuntu for a few months since I installed it.  The problem started a few days ago, I think after some updates.  I have strong signal (54MB/s) but the connection will lose itself and lose the stored password in the settings.  When I type the password in again in nm-applet it will connect again.  The performance has gone down to seem real slow for even text-only web pages, even though my connection is still 54MB/s.  It's intermittent connection losses, and usually after coming back from screen saver it has been lost already.  Is anybody else having this problem?  I don't know where to start about solving this problem.

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Amberx4"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:50:DB:C5   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.
```The driver is patched to allow packet injection for aircrack-ng.  This is not the problem though, has been working fine and I'm not cracking somebody else's wireless network it's my own network that is wireless with WPA2 Personal Key.

---

