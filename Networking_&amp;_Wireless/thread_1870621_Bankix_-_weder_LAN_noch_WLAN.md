---
title: "Bankix - weder LAN noch WLAN"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by flooo on 2011-10-27
Hi,

maybe a little less sleep in the last nights. Here my request in English:
I like the idea of a more safe online banking. That's why I trying to use Bankix right now. Unfortunately neither LAN nor WLAN is working - I have no idea why. On my system Kubuntu is running an both - LAN and WLAN - are working there. WLAN did not work from the start - it took some efforts, but at leas LAN was usable instantly.
I've got an Acer Aspire 4820TG with an Artheros AR8151 network device and an broadcom WLAN device. In this forum there are some threads with similar problems and drivers for that LAN device. I tried to install thos but during "make" I receive the following error (even within Kubuntu):
```
Linux Kernel Source not configure - missing autoconf.h
```
Using "modinfo atl1e" I think I receive on both systems the same answer:
```
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/atl1e/atl1e.ko
version:        1.0.0.7-NAPI
license:        GPL
description:    Atheros 1000M Ethernet Network Driver
author:         Atheros Corporation, <xiong.huang@atheros.com>, Jie Yang <jie.yang@atheros.com>
srcversion:     8C54D44E579979EF1C2E599
alias:          pci:v00001969d00001066sv*sd*bc*sc*i*
alias:          pci:v00001969d00001026sv*sd*bc*sc*i*
depends:        
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
parm:           tx_desc_cnt:Transmit description count (array of int)
parm:           rx_mem_size:memory size of rx buffer(KB) (array of int)
parm:           media_type:MediaType Select (array of int)
parm:           int_mod_timer:Interrupt Moderator Timer (array of int)
```

I'm looking forward any helpful answers. Thanks
Florian

I removed the german request!

---

### Post by flooo on 2011-10-30
Does no one has an idea - to my mind Bankix is based on Ubuntu.
Thanks
Florian

---

### Post by Dangertux on 2011-10-30
You need to prepare the kernel sources

```

sudo -s
cd /lib/modules/$(uname -r)/build/include/linux
ln -s ../generated/autoconf.h

```


If you don't have the kernel source downloaded you need to 

```

sudo apt-get install linux-source

```

hope this helps.

---

