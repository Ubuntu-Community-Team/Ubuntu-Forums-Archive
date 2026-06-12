---
title: "wireless woes"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by patanjali on 2009-11-14
Hello,

I have been motoring along with Kubuntu for a while now, and very happy with it.  Now my wireless has stopped working.  All checks out ok except when  run iwconfig I get

jack@phoenix:/etc/network$ iwconfig
lo        no wireless extensions.

vboxnet0  no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  [COLOR="Red"]Access Point: Not-Associated[/COLOR]
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I am using ndiswrapper with the Broadcom 4318 chipset (it has worked flawlessly for ages).

Can anyone help?

regards

patanjali

---

