---
title: "Change WIFI driver back to 11.10 version"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by roehre242 on 2012-04-29
Hi,
after the recent upgrade from 11.10 x64 to 12.04 x64 I'm facing some troubles with my Belkin WIFI dongle (pls see details below).

Bus 001 Device 002: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]

It was working quite well in 11.10 but after the upgrade it shows only 150Mbit Link Speed instead the 300Mbit in 11.10 and the connection also seems to have more latency as before. Unfortunately I have no exact test results which I can compare, but I have an old thunderbird mail box on a NAS which I have to connect to via WLAN (I know I should't do that). This was working under 11.10 but with 12.04 the connection stales mostly.

I noticed that in 12.04 the r8712u driver is used by default for the RTL8192 chipset.

How can I modify the driver mapping so that the old r8192su driver is used instead of r8712u?


Many thanks in advance for all your valuable replies.

---

### Post by chili555 on 2012-04-29
I hate when I do this to myself. I don't know the exact answer to your problem but I have some ideas we might explore. I have no idea if they'll work because I don't have your device nor a 300 Mb/s capable router, so I can't test.

I notice that r8712u has a number of mysterious loadable parameters and I wonder if any may be helpful:```
$ modinfo r8712u
filename:       /lib/modules/3.2.0-24-generic-pae/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     0FE0DF0FCF5D4304EC72F2C
<snip>
vermagic:       3.2.0-24-generic-pae SMP mod_unload modversions 686 
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)
```You can look at how these parameters are set in your system. ```
ls /sys/module/r8712u/parameters/
```Then see how a specific parameter is set (0? YES? 0x42???) with:```
cat /sys/module/r8712u/parameters/some_parameter
```I have looked for documentation in my system as well as on line and in a copy of rtl8712 I downloaded from Realtek. So far, I have not found any explanation.

You use these parameters temporarily with:```
sudo modprobe -r r8712u
sudo modprobe r8712u some_parameter=1  <--or whatever is called for
```Make it permanent with a conf file: /etc/modprobe.d/r8712u.conf:```
options r8712u some_parameter=1
```I will continue to search for a clearer description of these parameters and suggest you do the same.

Finally, I don't discount the possibility that the driver mis-reports the connection speed. I have seen such reports, but not specifically about r8712u that I recall.

I will especially be interested in:```
cat /sys/module/r8712u/parameters/ht_enable
```

----------
note to Chili: os_intfs.c ??

---

### Post by roehre242 on 2012-04-29
Hi,
thanks for your reply. Please see the parameter settings below:

/sys/module/r8712u/parameters/low_power
0
/sys/module/r8712u/parameters/power_mgnt
0
/sys/module/r8712u/parameters/rf_config
1
/sys/module/r8712u/parameters/ampdu_enable
1
/sys/module/r8712u/parameters/cbw40_enable
1
/sys/module/r8712u/parameters/ht_enable
0
/sys/module/r8712u/parameters/busy_thresh
40
/sys/module/r8712u/parameters/vcs_type
1
/sys/module/r8712u/parameters/vrtl_carrier_sense
2
/sys/module/r8712u/parameters/wmm_enable
0
/sys/module/r8712u/parameters/mp_mode
0
/sys/module/r8712u/parameters/channel
1
/sys/module/r8712u/parameters/network_mode
0
/sys/module/r8712u/parameters/hci
1
/sys/module/r8712u/parameters/lbkmode
0
/sys/module/r8712u/parameters/rfintfs
2
/sys/module/r8712u/parameters/chip_version
2
/sys/module/r8712u/parameters/video_mode
1
/sys/module/r8712u/parameters/initmac
(null)
/sys/module/r8712u/parameters/wifi_test
0
/sys/module/r8712u/parameters/ifname
wlan%d

I gave ht_enable=0 a try. It seems to lower the bit rate down to 54Mbit and shows improved signal, that's all.

---

### Post by chili555 on 2012-04-29
Sadly, I'm out of ideas. You might Google the driver and parameter and see what you can see.

Other than downloading from Realtek and compiling, always a touchy process, I know of no way to use the 10.10 module in 12.04.

---

### Post by Bainesy on 2012-04-29
After a quick search on why my Ethernet doesn't work in Ubuntu 12.04, but did in 10.04 and 10.10, i noticed that the realtek drivers for my motherboard Lan only go up to Linux kernel 2.6x... perhaps it's the same here? or are there some basic drivers somewhere that I/we don't know about?

---

### Post by chili555 on 2012-04-29
> **Bainesy said:**
> After a quick search on why my Ethernet doesn't work in Ubuntu 12.04, but did in 10.04 and 10.10, i noticed that the realtek drivers for my motherboard Lan only go up to Linux kernel 2.6x... perhaps it's the same here? or are there some basic drivers somewhere that I/we don't know about?I'm not sure we have the same issue. Do you have r8712u? The OP's wireless connects fine, just not super-fast.

---

### Post by Bainesy on 2012-04-30
> **chili555 said:**
> I'm not sure we have the same issue. Do you have r8712u? The OP's wireless connects fine, just not super-fast.

If that's the name of a driver I'm not sure, but my onboard Ethernet is RTL8111.
I started another thread but so far no-one has replied (apart from me) I'm gonna try a few more things see if I can get onto the net to get some drivers (hopefully)

and fair enough, didn't realise his was working, just not well... Guess that's what I get for not reading the whole thread ey.

---

### Post by roehre242 on 2012-05-03
I have to correct my previous statements: r8712u was already used in 11.10. I have booted from the live cd to check this. Driver and parameters are the same as in 12.04, but link speed shows correct 300Mbit. :confused:

---

### Post by chili555 on 2012-05-03
You could email Realtek or revert to 10.10. You might also file a bug: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

I'm sorry, I'm out of further suggestions.

---

