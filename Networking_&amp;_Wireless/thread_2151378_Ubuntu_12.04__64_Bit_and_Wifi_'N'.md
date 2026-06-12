---
title: "Ubuntu 12.04 / 64 Bit and Wifi 'N'"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by amtrakuk on 2013-06-04
Hi there.

I was wondering if there is a known issue with Ubuntu and the 802.11n WiFi standard.   The reason I ask, I had recently installed a brand new Intel 4965AGN 802.11 b/g/n Wifi Card into my laptop (using all 3 anteni), all seems fine (3-4 MB/Sec) except every so often the wireless drops out for a few seconds (and the app stops responding) then seems to resume before dropping out again.  Eventually getting so bad a reboot is needed.   The Wireless monitor along the top menu always reports as connected.

I am thinking this maybe a buffering issue.  Test perfomed are;

The drop out only occurs if using the WiFi intensivly (Copying large files etc) but for general browsing and the odd email it works fine,
Sat the laptop within a meter of the router, droput still occurs.
Tried the WiFi card in a windows 7 machine with no problems all day - no matter how much copying,
I have put the origional WiFi B/G card back in the laptop and that works fine,
Reinstalled ubuntu with 'N' Wireless card installed, made no difference in performance.

Has anyone else had this issue and does anyone have a workaround?

---

### Post by ahallubuntu on 2013-06-04
~

---

### Post by chili555 on 2013-06-04
> I think 4965AGN uses an older driver than iwlwifi. I'm not sure what the options are for that card. It uses iwl4965. The options are shown in modinfo:```
chili@Think410:~$ modinfo iwl4965
filename:       /lib/modules/3.8.0-23-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi 4965 driver for Linux
srcversion:     DBCE36D07FCAC1FB4C781FD
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.8.0-23-generic SMP mod_unload modversions 
[COLOR="#FF0000"]parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)[/COLOR]
```I also have seamless N speeds with my Intel Corporation Centrino Advanced-N 6200.

I suggest that the two of you look at how your router settings differ. Several of us have perfect N speeds and several struggle. I suspect that the router setup is at least a factor.

---

