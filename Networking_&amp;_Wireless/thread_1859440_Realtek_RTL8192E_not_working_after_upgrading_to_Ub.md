---
title: "Realtek RTL8192E not working after upgrading to Ubuntu 11.10"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by db654 on 2011-10-13
Hi all,

Earlier today I updated from 11.04 to 11.10 and upon reboot the wireless has stopped working :( At first, lsmod indicated that there was a conflict between 2 modules; r8192e_pci & rtl8192se. I have since then blacklisted the rtl8192se in /etc/modules/blacklist.conf but I still have no wifi...

Here is the output from some useful commands:
```
**lspci -nvn | grep 8192**
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
    Kernel modules: r8192e_pci, rtl8192se

**lsmod | grep 8192**
r8192e_pci            234316  0 

**modinfo r8192e_pci **
filename:       /lib/modules/3.0.0-12-generic-pae/kernel/drivers/staging/rtl8192e/r8192e_pci.ko
description:    Linux driver for Realtek RTL819x WiFi cards
version:        V 1.1
license:        GPL
firmware:       RTL8192E/data.img
firmware:       RTL8192E/main.img
firmware:       RTL8192E/boot.img
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
srcversion:     2034A982846FE0B5FC00A69
alias:          pci:v000007AAd00000047sv*sd*bc*sc*i*
alias:          pci:v000007AAd00000044sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        
staging:        Y
vermagic:       3.0.0-12-generic-pae SMP mod_unload modversions 686 
parm:           debug:debug output mask (int)
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           hwwep: Try to use hardware WEP support. Still broken and not available on all cards (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

**dmesg | grep rtl**
[   23.810423] rtl819xE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.810431] rtl819xE 0000:02:00.0: setting latency timer to 64
[  820.340490] rtl819xE:ERR!!! NicIFEnableNIC(): Driver is already down!
[  820.340495] rtl819xE:SetRFPowerState8190(): NicIFEnableNIC failed
[  820.340500] rtl819xE:ERR!!! NicIFEnableNIC(): Driver is already down!
[  820.340502] rtl819xE:SetRFPowerState8190(): NicIFEnableNIC fai

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**iwlist wlan0 scan**
wlan0     No scan results
```I would be very grateful if anyone has any suggestions or solutions for this problem!
Cheers,
Dan 

EDIT: Solved - before the update I had been using wicd , but when I updated, network manager was reinstalled which must have caused a conflict. Uninstalling wicd seemed to solve the problem!

---

