---
title: "Where did rtap0 go in iwl3945?"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by jeffmefun on 2009-09-16
Trying to set up a parallel monitoring interface and not having much luck.

Current version of iwl3945 has no parm: for it (below).

Any suggestions for how to get the rtap0 up and running? I'm willing to recompile, do whatever, but not even sure how far back to go, etc. Already tried the backports for jaunty, but didn't have any luck there.

root@ubuntu:~# modinfo iwl3945
filename:       /lib/modules/2.6.28-15-generic/updates/iwl3945.ko
firmware:       lbm-iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.2.26ks
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     6D2DCA16AE42ED29975784D
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        lbm_cw-mac80211,iwlcore,led-class,lbm_cw-cfg80211
vermagic:       2.6.28-15-generic SMP mod_unload modversions 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using software crypto (default 1 [software])
 (int)
parm:           debug:debug output mask (uint)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           fw_restart3945:restart firmware in case of error (int)

---

### Post by jeffmefun on 2009-09-23
bump - any help is most appreciated - thanks!

---

