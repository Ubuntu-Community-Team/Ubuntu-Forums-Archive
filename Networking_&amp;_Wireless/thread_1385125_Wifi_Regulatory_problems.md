---
title: "Wifi Regulatory problems"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by jjmerelo on 2010-01-19
Hi,
Still here with the same problem. I'm using ubuntu 9.10, 2.6.31-17-generic kernel, with an Intel WiFi Link 5100 controller on a Sony Vaio VGN-SR29VN.
WiFi with WEP and open works fine, but when I try to connect using WPA/WPA2, I get errors of this kind:
> cfg80211: Calling CRDA for country: ES
[   31.753670] cfg80211: Received country IE:

Which seems to be that my machine is defined as being in IE instead of Spain... and then
> [   31.753678] cfg80211: CRDA thinks this should applied:
[   31.753679] cfg80211: Regulatory domain: ES
which is exactly as I have defined it in /etc/modprobe.d/cfg80211.conf
and then
> cfg80211: We intersect both of these and get:
[   31.753691] cfg80211: Regulatory domain: 98
and finally, disconnection:
> cfg80211: Current regulatory domain updated by AP to: ES
[   31.753744] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   31.753746] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   35.343067] wlan0: disassociating by local choice (reason=3)

I have tried to install and use iw, issuing iw reg set IE, ES and everything else, but it plainly does not work.

Thanks for any help.

Cheers

JJ

---

