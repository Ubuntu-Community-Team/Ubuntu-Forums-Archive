---
title: "Wireless sleeping after long wait - vmnetbridge?"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by rapachooie on 2009-04-01
Hi all,

I have this issue on my laptop....

Essentially, when I close the lid (which just turns the screen on), and leave it alone for a while, after around 30m-1h the wireless disconnects and wont reconnect... it will keep trying and continue to ask me for the network key... if I disable the wireless and then reenable it again, it does not detect the network which suggests to me that the network card is sleeping or is off and cannot be reactivated by the network manager (standard).

I am looking at /var/log/syslog and the kernel has alot of these entries (after shutdown/startup which fixes the issue)...

"vmnetBridge: Can't remove interface wlan0 4 (does not exist). "

The log is also showing a bit of:

"WARNING: at /build/buildd/linux-backports-modules-2.6.27-2.6.27/debian/build/build-generic/compat-wireless-2.6/net/mac80211/main.c:232 ieee80211_hw_config+0x85/0x90 [lbm_cw_mac80211]()"

Which I just dont understand... Im quite new to this...

Im wondering if this might be one of the causes or related to the issue, of if it is a simple issue found elsewhere?

Thanks in advance

---

