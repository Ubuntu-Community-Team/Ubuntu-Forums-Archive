---
title: "Ruined wireless with aircrac-ng... stupid, i know"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by jman594 on 2009-06-18
I completele ruined my wireless setup trying to get aircrack-ng working. I suppose that was dumb, but i needed a way to do some pen-testing on the cheap. Now it's costing me time. 

Here's the down and dirty:

1. I followed the guide on aircrack-ng's site to install the drivers and patches for my nic
2. After reboot, i no longer have the option to enable wireless on my network system try icon (sorry, dont' know what to call it. I'm beginning to migrate from M$ to *nix).
3. lspci gives me my nic as:
         a. 02:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
4. Here is what i found from teh dmesg as it pertains to ipw2200:
         a. [    9.426059] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[    9.426373] ipw2200: Unknown symbol ieee80211_wx_set_encode
[    9.426460] ipw2200: Unknown symbol ieee80211_wx_get_encode
[    9.426770] ipw2200: Unknown symbol ieee80211_txb_free
[    9.426908] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[    9.427225] ipw2200: Unknown symbol ieee80211_wx_get_scan
[    9.427309] ipw2200: Unknown symbol escape_essid
[    9.427477] ipw2200: Unknown symbol ieee80211_freq_to_channel
[    9.427666] ipw2200: Unknown symbol ieee80211_networks_age
[    9.428053] ipw2200: Unknown symbol ieee80211_set_geo
[    9.428478] ipw2200: Unknown symbol ieee80211_rx
[    9.428725] ipw2200: Unknown symbol ieee80211_channel_to_index
[    9.429305] ipw2200: Unknown symbol ieee80211_rx_mgt
[    9.429392] ipw2200: Unknown symbol ieee80211_get_geo
[    9.429542] ipw2200: Unknown symbol free_ieee80211
[    9.429964] ipw2200: Unknown symbol ieee80211_is_valid_channel
[    9.430176] ipw2200: Unknown symbol alloc_ieee80211

5. I have no idea how bad i screwed this up. Do i need to re-install the OS? Cause that would suck.



Thanks for your time guys. I just want to go back to the way things were before i bricked my wireless nic. oh, btw, the wireless nic used to be eth1 and now when doing a ifconfig, it's gone (go figure).

...

---

### Post by NoOne121 on 2009-06-18
not the first to do this...and not the last either...;)

might help if we knew exactly what you did...i assume you installed the ipw2200 drivers?
what hgappens with ....sudo modprobe ipw2200

i reinstalled jaunty using the synaptic package manager after i did something pretty similar to yourself...lol...but that would be a desperation move.




****

---

### Post by jman594 on 2009-06-18
Thanks a ton for the quick response!!

$ sudo modprobe ipw2200
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: Could not open '/lib/modules/2.6.28-11-generic/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-11-generic/kernel/net/ieee80211/ieee80211.ko': No such file or directory
FATAL: Error inserting ipw2200 (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Just in case, here is:

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:15:60:ad:fe:04
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751m-v3.29a ip=192.168.1.103 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:92:e9:81:79:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


Yeah. I think aircrack-ng is a spoof site for pwning n00b's. 


Anything else, lemme know!!

---

### Post by carcar1 on 2009-06-20
we need your

```
iwconfig
```

could be your monitor mode is just turned on knocking out connections and internet.

use

```
sudo ifconfig devid down
```

then 

```
sudo iwconfig devid mode managed
```

and that should fix monitor mode if thats what it is

---

### Post by jman594 on 2009-06-22
So, it's probably not helpful to others that have made the awful decision to tinker with aircrack-ng without knowing how to back out, but I just bit the bullet and backed-up then re-installed the OS. I wasn't too far into my Ubuntu experience that I couldn't easily add everything I used to have back. I'm sure I'll forget something, but at least I have a completely fresh OS and not one with a bricked wireless nic. ;-)

Thanks for all your help guys!:D

---

