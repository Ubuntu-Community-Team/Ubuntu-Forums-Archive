---
title: "Intel PRO 4965 AG or AGN: Wireless Network unclaimed"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by claydon on 2013-04-23
Hi All, 

Hope you can help. I have had a read through other posts about this kind of problem but the fixes in them posts do not seem to work, so I am hoping you can. I have a HP Compaq 8710w Laptop that I have just installed 32bit Ubuntu 12.10 on. Everything works fine apart from the onboard wireless. 

As per other threads I will post this 

lshw -C Network

```

 *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1b:38:88:5c:dc
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.3-0 ip=172.16.10.205 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:e8020000-e803ffff memory:e8040000-e8040fff ioport:5040(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:e4000000-e4001fff

```


As you can see the wireless adapter shows up as being unclaimed. I read in a post that this is normally because the physical wireless button is not on. I do have this on (the bluetooth shows up as working when its pressed).

Could someone please point me in the right direction to get this up and running. If you need any output from other commands just reply and I will paste them up. 

Thanks a bunch

---

### Post by ukbeast on 2013-04-23
Sounds like you may have a Broadcom WLAN driver, check this guide [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by steeldriver on 2013-04-23
I don't think so...

```
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: [COLOR=#0000ff]**Intel Corporation**[/COLOR]

```

I have the same device in this Thinkpad and it works fine in 12.04 using the iwl4965 driver module - I wonder what's changed? What does

```
lsmod | grep ^iwl
```

say? what about

```
modinfo iwl4965
```

---

### Post by claydon on 2013-04-23
Hi Thanks for the Replies, 


lspci shows

```

10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```


lsmod | grep ^iwl

```

iwl4965               106889  0 iwlegacy               87811  1 iwl4965

```


modinfo iwl4965

```

filename:       /lib/modules/3.5.0-27-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi 4965 driver for Linux
srcversion:     45405E1F5D748B660BD125B
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.5.0-27-generic SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)

```

---

### Post by steeldriver on 2013-04-23
Hmm, all looks OK so far - I hope I am not leading you down a rabbit hole here - anything interesting in syslog?

```
grep iwl /var/log/syslog
```

I think if it was a hardware switch issue you'd see 'DISABLED' instead of 'UNCLAIMED'

I'm leery of trying to help since I don't have any experience with the 3.5.x kernels

---

### Post by ahallubuntu on 2013-04-23
~

---

### Post by claydon on 2013-04-23
Hey, I think you might be onto something. Finally an error that I haven't seen before


```

Apr 22 23:45:46 L076467-Linux kernel: [    9.588238] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:Apr 22 23:45:46 L076467-Linux kernel: [    9.588240] iwl4965: Copyright(c) 2003-2011 Intel Corporation
Apr 22 23:45:46 L076467-Linux kernel: [    9.588323] iwl4965 0000:10:00.0: >Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
Apr 22 23:45:46 L076467-Linux kernel: [    9.629462] iwl4965 0000:10:00.0: >Unsupported (too old) EEPROM VER=0x36 < 0x2f CALIB=0x0 < 0x5
Apr 22 23:45:46 L076467-Linux kernel: [    9.629514] iwl4965: probe of 0000:10:00.0 failed with error -22

```

Going to google this and see what shows up, but if you have any idea how to fix this I would be happy to hear :) 

Thanks again

---

### Post by ahallubuntu on 2013-04-23
~

---

### Post by claydon on 2013-04-23
Looks like I won't be getting this working. Seems these cards are pre-production cards that shouldn't have made it into production laptops... I actually found an ubuntu archive from yourself ahallubuntu where the person couldn't get it fixed. Guess I'll try find a compatible PCMCIA card and just use that. 

Thanks for the help

---

### Post by ahallubuntu on 2013-04-23
~

---

### Post by chili555 on 2013-04-23
Unfortunately, Ebay is where most of the bad eeprom Intel cards come from. I might be interested in a card pulled from a working laptop with a return policy and a zillion feedback score 99% seller, but not otherwise. Dr. Chili recommends you always Ebay responsibly.

---

