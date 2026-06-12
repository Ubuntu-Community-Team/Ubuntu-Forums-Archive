---
title: "HSO module (Natty Narwhal)"
date: 2011-03-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by alexfish on 2011-03-27
hi

I am looking some info for HSO module (ref Natty Narwhal )

and referenced to earlier Kernel 2.6.35 (hso.ko) 
according to [http://lxr.linux.no/#linux+v2.6.35/drivers/net/usb/hso.c#L101](http://lxr.linux.no/#linux+v2.6.35/drivers/net/usb/hso.c#L101), the device ID's are incomplete (there for would require patches ) , the  patch from pharscape only go to Kernel 2.6.34

so am looking for the modinfo of the module in Natty

```
modinfo hso
```thanks in advance

alex

---

### Post by lucazade on 2011-03-27
> **alexfish said:**
> hi

I am looking some info for HSO module (ref Natty Narwhal )

and referenced to earlier Kernel 2.6.35 (hso.ko) 
according to [http://lxr.linux.no/#linux+v2.6.35/drivers/net/usb/Kconfig#L361](http://lxr.linux.no/#linux+v2.6.35/drivers/net/usb/Kconfig#L361) , the device ID's are incomplete (there for would require patches ) , the  patch from pharscape only go to Kernel 2.6.34

so am looking for the modinfo of the module in Natty

```
modinfo hso
```

thanks in advance

alex

```
$ modinfo hso
filename:       /lib/modules/2.6.38-7-generic/kernel/drivers/net/usb/hso.ko
license:        GPL
description:    USB High Speed Option driver
author:         Option Wireless
srcversion:     5555EFC13A42727077E4326
alias:          usb:v0AF0pC100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD058d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD357d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD157d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD057d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD255d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD155d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD055d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD035d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p9000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8900d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8800d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8400d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7A05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7A01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7601d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7501d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7401d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7381d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7361d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7301d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pC031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7311d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7271d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7251d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7211d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7111d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6971d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6951d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6911d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6791d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6771d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6751d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6711d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.38-7-generic SMP mod_unload modversions 686 
parm:           debug:Level of debug [0x01 | 0x02 | 0x04 | 0x08 | 0x10] (int)
parm:           tty_major:Set the major tty number (int)
parm:           disable_net:Disable the network interface (int)

```

---

### Post by alexfish on 2011-03-27
> **lucazade said:**
> ```
$ modinfo hso
filename:       /lib/modules/2.6.38-7-generic/kernel/drivers/net/usb/hso.ko
license:        GPL
description:    USB High Speed Option driver
author:         Option Wireless
srcversion:     5555EFC13A42727077E4326
alias:          usb:v0AF0pC100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD058d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD357d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD157d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD057d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD255d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD155d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD055d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD035d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p9000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8900d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8800d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8400d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p8200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7A05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7A01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7601d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7501d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7401d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7381d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7361d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7301d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pD013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0pC031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7311d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7271d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7251d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7211d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7111d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p7011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6971d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6951d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6911d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6791d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6771d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6751d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0AF0p6711d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.38-7-generic SMP mod_unload modversions 686 
parm:           debug:Level of debug [0x01 | 0x02 | 0x04 | 0x08 | 0x10] (int)
parm:           tty_major:Set the major tty number (int)
parm:           disable_net:Disable the network interface (int)

```

hi

thanks , looks as only diff in (f/lib/modules/2.6.35-27-generic/kernel/drivers/net/usb/hso.ko)
480        {USB_DEVICE(0x0af0, 0x9000)},

can assume Natty module OK

alex

---

