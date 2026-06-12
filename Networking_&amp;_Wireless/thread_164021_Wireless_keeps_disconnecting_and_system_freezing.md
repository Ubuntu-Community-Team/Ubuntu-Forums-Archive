---
title: "Wireless keeps disconnecting and system freezing"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by siwilks on 2006-04-22
Hi there,

I'm running a tnet1130 based card using ndiswrapper and it's been fine for months but now it has trouble staying connected to the access point and I'll have to either redo "sudo iwconfig wlan0 essid ..." or else deactivate and reactivate it in the networking applet. When I do this sometimes it has reconnected and sometimes it hasn't but often my whole system will freeze within a couple of minutes subsequent to this and I'll have to reboot my computer. Any help wold be VERY gratefully received.

Oh, and here's the output of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:BF:1B:C3:30
          Bit Rate:48 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:100/100  Signal level:-73 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

