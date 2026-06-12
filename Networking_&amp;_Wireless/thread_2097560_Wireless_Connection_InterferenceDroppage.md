---
title: "Wireless Connection Interference/Droppage"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by chines on 2012-12-23
I've recently installed Ubuntu 12.04 on my old HP laptop in the hopes of extending its usefulness for a little while longer.  Unfortunately, I'm having some fairly irritating problems in the wireless department.  Specifically, the wireless connection drops out every ten minutes or so (typically only when active, such as during downloads, during system updates, or when watching something on YouTube) before struggling to reconnect and/or deciding to ask me to re-enter network credentials.  

To make matters worse, this network cutout affects every other device in my house - my iMac, my parents' computer, the upstairs Blu-Ray player, you name it.  I'm sure it's not the ISP or router itself causing the issue, because this is only a problem when I'm running Linux - it has never happened otherwise.  This leads me to believe it's an issue with my wireless card or the associated drivers.  I spent nearly half of yesterday trying to fix the problem, but have thus far had no success.

Now before I get into other, problem-related details, I should probably list some system specs and show the results I'm getting from related commands.  Please bear in mind that, though I have tried to do my research here, I am a relative newb to the whole Linux thing and so do not fully understand all the readouts: 

Wireless card: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev02)
Security: WPA/WPA2.
Build: Ubuntu 12.04 LTS.
IPv6: not enabled.

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:1b:38:31:05:ac
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.121 firmware=5753m-v3.56 latency=0 multicast=yes  port=twisted pair
       resources: irq:46 memory:f4100000-f410ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:65:50:4c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-29-generic-pae firmware=15.32.2.9 ip=10.0.0.4 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:f4000000-f4000fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"@Home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:2A:62:08:24   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:39  Invalid misc:2870   Missed beacon:0

eth0      no wireless extensions.

modinfo iwl3945
filename:       /lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <[EMAIL="ilw@linux.intel.com"]ilw@linux.intel.com[/EMAIL]>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     301B04B4010DED41B0830D0
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwl-legacy,cfg80211,mac80211
intree:         Y
vermagic:       3.2.0-29-generic-pae SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

Now, in the threads I've seen, anyone with the same wireless card and similar problems has been referred to one of three solutions.  The first, to install a kernel driver, I have unsuccessfully attempted, perhaps because I am unsure of certain commands.  The second, to turn off the wireless power settings, is ineffective because (as you can probably see above) said settings are already off.  And the third, being related to a completely separate build of Linux, was irrelevant.  

Another thing I note is this mention of 'superuser' status under the lshw -C command above, which I do not know how to access (or whether I ought to given my limited knowledge).  Now I know that 'root' is the deep-level system access, deeper than the users' credentials or than an Administrator on a Windows machine; I'm guessing that 'superuser' is similar, but less so.  What to do with that information, however, I have no idea.

Based on what you see here, what steps would you recommend I take to further diagnose this issue and/or find some sort of solution?  I truly appreciate any and all suggestions.

---

