---
title: "Intel 5300 AGN wireless card, 11n-mode doesn't work !?"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by dut123 on 2009-08-29
Hi!

My Intel 5300 AGN wireless card works only if I do

```
sudo modprobe -r iwlagn
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1
```Otherwise connection is extremely slow (takes minutes to load a webpage) or does not work at all. 

If I'm not mistaken the options above mean that 802.11n mode is disabled. Is there a way to get this mode work, too? (My wireless router supports 11n) On windows I have speeds up to 130 MB/s, iwconfig shows only up to 54 MB/s: 

iwconfig gives (after sudo modprobe iwlagn 11n_disable=1 11n_disable50=1)
```

wlan0     IEEE 802.11abg  ESSID:"DWLAN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:CB:D4:74:40   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```I googled for hours and didn't find a solution. My system is ubuntu-jaunty kernel image 2.6.28-15, i have linux-backport-modules-jaunty and linux-backport-modules-jaunty-generic installed because 'google said' that this packages might solve my problem (but I don't unterstand why). 

The only google result I have found promising was:

[http://bbs.archlinux.org/viewtopic.php?id=70492](http://bbs.archlinux.org/viewtopic.php?id=70492)

but I didn't manage to apply the suggested solution, 

crda seems to be installed:
```
aptitude search crda
i A wireless-crda                   - Wireless Central Regulatory Domain Agent

```but /etc/conf.d/wireless-regdom and /etc/rc.conf do not exist



I also installed kernel version  2.6.30-02063005-generic from mainline, it didn't help I think. 

```
 modinfo iwlagn
filename:       /lib/modules/2.6.28-15-generic/updates/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       lbm-iwlwifi-4965-2.ucode
firmware:       lbm-iwlwifi-5150-2.ucode
firmware:       lbm-iwlwifi-5000-1.ucode
firmware:       iwlwifi-6050-2.ucode
firmware:       iwlwifi-6000-2.ucode
srcversion:     BCCD91E619EB3B155A9821E
alias:          pci:v00008086d00000084sv*sd*bc*sc*i*
alias:          pci:v00008086d00000083sv*sd*bc*sc*i*
alias:          pci:v00008086d00000089sv*sd*bc*sc*i*
alias:          pci:v00008086d00000088sv*sd*bc*sc*i*
alias:          pci:v00008086d00000087sv*sd*bc*sc*i*
alias:          pci:v00008086d00000086sv*sd*bc*sc*i*
alias:          pci:v00008086d00000085sv*sd*bc*sc*i*
alias:          pci:v00008086d00000082sv*sd*bc*sc*i*
alias:          pci:v00008086d00004238sv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001122bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001112bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001102bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,lbm_cw-mac80211,lbm_cw-cfg80211
vermagic:       2.6.28-15-generic SMP mod_unload modversions 
parm:           disable50:manually disable the 50XX radio (default 0 [radio on]) (int)
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           debug50:50XX debug output mask (uint)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (uint)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)
```Notice that modinfo iwlagn gives version 1.3.27k (without s) if I boot with kernel 2.6.30

Any ideas ? Perhaps it could be important to say that I live in Germany, because frequency standards may be different in different countries. By the way, sorry for my bad english ;-). 

Thanks in advance

dut123

---

### Post by manus_eiffel on 2009-09-11
I think this is related to:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/384924](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/384924)

When  I did what you suggested, although the connexion was not great, I went from about 20% packet loss down to less than 5%.

---

