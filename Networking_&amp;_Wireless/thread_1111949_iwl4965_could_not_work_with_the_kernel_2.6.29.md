---
title: "iwl4965 could not work with the kernel 2.6.29"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by Kelen.Chang on 2009-03-31
i compiled kernel 2.6.29, most of everything is okay, but the wireless could not work.
this is available option relation with iwl 
```
$ grep -v "^#" ./.config |grep -i iwl
CONFIG_IWLWIFI=m
CONFIG_IWLCORE=m
CONFIG_IWLWIFI_LEDS=y
CONFIG_IWLAGN=m
CONFIG_IWLAGN_SPECTRUM_MEASUREMENT=y
CONFIG_IWLAGN_LEDS=y
CONFIG_IWL4965=y
```
and after load in system. i checked hardware with command lshw -C network, 
```
$ lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:00:c1:c1
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
```

so, anyone could help me?

---

### Post by chili555 on 2009-03-31
> $ lshw -C network
  *-network DISABLEDDISABLED usually means that either the hardware switch on the front of the laptop or elsewhere is switched off; or, that the usual key combination, Fn+F5, for example, has not been pressed. Please check.

---

### Post by Kelen.Chang on 2009-03-31
chili555,
but it's worked for me on auto upgraded kernel 2.6.24-23.

---

### Post by Kelen.Chang on 2009-03-31
chili555,
but it's worked for me on auto upgraded kernel 2.6.24-23.

---

### Post by chili555 on 2009-03-31
So what do the logs say about it? Please do:```
sudo cat /var/log/messages | grep -i kill
```Thanks.

---

### Post by Kelen.Chang on 2009-03-31
chili555, i tried Fn+F5 just switched kernel 2.6.29, wirelee worked. thanks a lot.

---

