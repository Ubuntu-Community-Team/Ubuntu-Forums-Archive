---
title: "Latest linux image push (2.6.32-25) causing WLAN to drop"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by jgmillr1 on 2010-09-08
I noticed this weekend that I began experiencing wireless issues with the NIC (Intel 5300) on my laptop. I have had no problems with the wireless using several Ubuntu versions. This began after I installed the packages associated with the Update Manager last Friday, which included the 2.6.32-25.43 kernel update.

My wireless will drop out anywhere from 10 seconds to a couple minutes later after connecting to my router. Again, I have not have any wireless issues before. 

Has anyone else experienced this issue? What other information would be helpful for understanding/resolving the problem? Thanks in advance.

Below is the end of dmesg when I enable the device.

[ 1220.725229] Registered led device: iwl-phy0::radio
[ 1220.725372] Registered led device: iwl-phy0::assoc
[ 1220.725883] Registered led device: iwl-phy0::RX
[ 1220.726422] Registered led device: iwl-phy0::TX
[ 1220.749395] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1228.969542] wlan1: deauthenticating from 00:24:01:f5:b8:b0 by local choice (reason=3)
[ 1229.008433] wlan1: direct probe to AP 00:24:01:f5:b8:b0 (try 1)
[ 1229.013540] wlan1: direct probe responded
[ 1229.013549] wlan1: authenticate with AP 00:24:01:f5:b8:b0 (try 1)
[ 1229.016045] wlan1: authenticated
[ 1229.016141] wlan1: associate with AP 00:24:01:f5:b8:b0 (try 1)
[ 1229.020485] wlan1: RX AssocResp from 00:24:01:f5:b8:b0 (capab=0x421 status=0 aid=4)
[ 1229.020493] wlan1: associated
[ 1229.024539] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1239.484122] wlan1: no IPv6 routers present
[ 1248.585510] iwlagn 0000:03:00.0: iwl_tx_agg_start on ra = 00:24:01:f5:b8:b0 tid = 0

---

### Post by jgmillr1 on 2010-09-10
Looks like the WLAN dropping is unrelated to the kernel update (Whew). Apparently I was having issues with my wireless router, which are now resolved though I still don't have a firm understanding of what triggered it.

---

