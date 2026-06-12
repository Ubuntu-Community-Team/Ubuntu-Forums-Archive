---
title: "RT2860 Pcie Question RT2860sta or RT2800pci"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by ZZRabbit on 2011-09-20
Hi all

I was just wondering why both modules rt2860sta & rt2800pci are loading, in 11.04.

I have no real problems with G but N is crap on 2 pcs both with the Ubuntu and the same wireless card Asus PCE-N13.

---

### Post by praseodym on 2011-09-20
rt2800pci is developed at the moment (11.04), so it is newer...

---

### Post by chili555 on 2011-09-20
In my experience, rt2800pci gives poor or no performance and needs to be blacklisted so that rt2860sta drives your card.

---

### Post by ZZRabbit on 2011-09-21
Hi all

I blacklisted the rt2800pci. The rt2860sta seems to be more stable by itself, but it only connects G, not N.

Just wondering if I'm missing something.:confused:

thanx

ZZ

---

### Post by praseodym on 2011-09-21
What device is that in detail:

```
lspci -nnk | grep -iA2 net
```

---

### Post by ZZRabbit on 2011-09-21
lspci -nnk | grep -iA2 net

Output:

06:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]
	Subsystem: ASUSTeK Computer Inc. Device [1043:130f]
	Kernel driver in use: rt2860

thanx
ZZ

---

### Post by praseodym on 2011-09-21
Please show:

```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```

---

### Post by ZZRabbit on 2011-09-21
I don't have the RT2860STA.dat.

The rt2860sta module in 11.04 doesn't look for the dat file, like the older version does.

This was a fresh install of 11.04 and from the beginning both modules have been loading.

Thanx
ZZ

---

### Post by praseodym on 2011-09-21
Which version is that? Normally you need that file for Draft-N:

```
modinfo rt2860sta
```

---

### Post by ZZRabbit on 2011-09-21
modinfo rt2860sta

Output

filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       rt3090.bin
firmware:       rt2860.bin
srcversion:     C22EE7282F9A519D7E9A764
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.38-11-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)


ZZ

---

### Post by praseodym on 2011-09-21
Driver version 2.1.0.0 is old, try the attached one (version 2.4.0.0). There is a rt2860sta.dat you can modify before compiling, the file **/os/linux/config.mk** is already modified.

The modifications for rt2860sta.dat in comparison to the original file are:

```
#Default
CountryRegion=1
CountryRegionABand=1
CountryCode=DE                                                    
ChannelGeography=1                                               
SSID=<youressid>                                                 
NetworkType=Infra                                                
WirelessMode=5                                          
Channel=yourchannel                                               
AuthMode=WPAPSK
EncrypType=AES
WPAPSK=< your wpa2-password >
HT_BW=1
```
These settings are for germany, you need to add your ESSID, your key, etc.

---

### Post by ZZRabbit on 2011-10-17
Hi all again

I have 2 Asus PCE-N13 wireless adapters, one in my system and one in my wife's system.

We had the same problem with them in Ubuntu 11.04 with the rt2800pci module. So praseodym gave the vendors source code for the rt2860sta module version 2.4 that fixed the problem.

Now having upgraded to ubuntu 11.10 the problem is back, and now the rt2860sta is gone. So I am at a dead end.

Ok here is what happens, if I'm conected I can go everywhere but my wife can't go anywhere, if I disconnect she can go everywhere. Can I still use the 2.4 rt2860sta in 11.10.


Thanx

ZZ :(

---

### Post by praseodym on 2011-10-17
Do you have a MAC-address filter activated in your router? Try the rt3090sta

---

### Post by ZZRabbit on 2011-10-17
> **praseodym said:**
> Do you have a MAC-address filter activated in your router? Try the rt3090sta

No MAC-address filtering is turned off.

ZZ

---

