---
title: "Digi-TV card does not work after resume from suspend"
date: 2009-07-26
forum: Multimedia Software
---

### Post by jis on 2009-07-26
The card works after boot, but not after resume from suspend. What can you do?

By lspci:
02:08.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)

By dmesg after running kaffeine after resume:
[ 3877.820075] tda1004x: found firmware revision ff -- invalid
[ 3877.820083] tda1004x: waiting for firmware upload (dvb-fe-tda10045.fw)...
[ 3877.820090] budget_ci dvb 0000:02:08.0: firmware: requesting dvb-fe-tda10045.fw
[ 3878.268070] tda1004x: Error during firmware upload
[ 3878.268101] tda1004x: firmware upload failed

$ locate dvb-fe-tda10045.fw
/lib/firmware/dvb-fe-tda10045.fw

---

### Post by ddrichardson on 2009-07-26
Assuming its the tda1004x kernel module, suspend the module so it's forced to reload on resume.

---

### Post by ddrichardson on 2009-07-26
I'm not on an Ubuntu box at the moment but the file is /etc/pm/config.d/modules in Archlinux so is most likely the same or in /etc/acpi in Ubuntu.  You would add a line:
```
SUSPEND_MODULES="modulename"
```

---

### Post by jis on 2009-07-26
How do you suspend such a module?

---

### Post by jis on 2009-07-26
I put file called modules in /etc/pm/config.d
There I wrote ```
SUSPEND_MODULES="$SUSPEND_MODULES tda1004x"
```. It did not help.

---

### Post by ddrichardson on 2009-07-26
That's malformed unless SUSPEND_MODULES is already defined:```
SUSPEND_MODULES="tda1004x"
```Like I said though, you need to find the module, I'm guessing from dmesg. ```
lsmod | grep dvb
```Might help.

---

### Post by jis on 2009-07-27
What is the module?

Here's some data:
> $ lsmod | grep dvb
dvb_core               92032  2 budget_ci,budget_core
jarno@workstation:/etc/pm/config.d$ modinfo dvb_core
filename:       /lib/modules/2.6.28-14-generic/kernel/drivers/media/dvb/dvb-core/dvb-core.ko
license:        GPL
author:         Marcus Metzler, Ralph Metzler, Holger Waechtler
description:    DVB Core Driver
srcversion:     5C43EFB33EC34B066DE9A06
depends:        
vermagic:       2.6.28-14-generic SMP mod_unload modversions 586 
parm:           dvb_net_debug:enable debug messages (int)
parm:           frontend_debug:Turn on/off frontend core debugging (default:off). (int)
parm:           dvb_shutdown_timeout:wait <shutdown_timeout> seconds after close() before suspending hardware (int)
parm:           dvb_force_auto_inversion:0: normal (default), 1: INVERSION_AUTO forced always (int)
parm:           dvb_override_tune_delay:0: normal (default), >0 => delay in milliseconds to wait for lock after a tune attempt (int)
parm:           dvb_powerdown_on_sleep:0: do not power down, 1: turn LNB voltage off on sleep (default) (int)
parm:           dvb_mfe_wait_time:Wait up to <mfe_wait_time> seconds on open() for multi-frontend to become available (default:5 seconds) (int)
parm:           cam_debug:enable verbose debug messages (int)
parm:           debug:Turn on/off debugging (default:off). (int)
parm:           dvbdev_debug:Turn on/off device debugging (default:off). (int)
jarno@workstation:/etc/pm/config.d$ modinfo budget_ci
filename:       /lib/modules/2.6.28-14-generic/kernel/drivers/media/dvb/ttpci/budget-ci.ko
description:    driver for the SAA7146 based so-called budget PCI DVB cards w/ CI-module produced by Siemens, Technotrend, Hauppauge
author:         Michael Hunold, Jack Thomasson, Andrew de Quincey, others
license:        GPL
srcversion:     D6F7A6F591D1A5ECE1C0A4C
alias:          pci:v00001131d00007146sv000013C2sd0000101Abc*sc*i*
alias:          pci:v00001131d00007146sv000013C2sd00001017bc*sc*i*
alias:          pci:v00001131d00007146sv000013C2sd00001012bc*sc*i*
alias:          pci:v00001131d00007146sv000013C2sd00001011bc*sc*i*
alias:          pci:v00001131d00007146sv000013C2sd00001010bc*sc*i*
alias:          pci:v00001131d00007146sv000013C2sd0000100Fbc*sc*i*
alias:          pci:v00001131d00007146sv000013C2sd0000100Cbc*sc*i*
depends:        dvb-core,budget-core,ir-common,saa7146
vermagic:       2.6.28-14-generic SMP mod_unload modversions 586 
parm:           rc5_device:only IR commands to given RC5 device (device = 0 - 31, any device = 255, default: autodetect) (int)
parm:           ir_debug:enable debugging information for IR decoding (int)
parm:           adapter_nr:DVB adapter numbers (array of short)
jarno@workstation:/etc/pm/config.d$ modinfo budget_core
filename:       /lib/modules/2.6.28-14-generic/kernel/drivers/media/dvb/ttpci/budget-core.ko
license:        GPL
srcversion:     D0DE1EB94E22D6CB8BABE41
depends:        saa7146,dvb-core,ttpci-eeprom
vermagic:       2.6.28-14-generic SMP mod_unload modversions 586 
parm:           debug:Turn on/off budget debugging (default:off). (int)
parm:           bufsize:DMA buffer size in KB, default: 188, min: 188, max: 1410 (Activy: 564) (int)
jarno@workstation:/etc/pm/config.d$ modinfo tda1004x
filename:       /lib/modules/2.6.28-14-generic/kernel/drivers/media/dvb/frontends/tda1004x.ko
license:        GPL
author:         Andrew de Quincey & Robert Schlabbach
description:    Philips TDA10045H & TDA10046H DVB-T Demodulator
srcversion:     EF4B2CB6B6A3E9BAA73AC07
depends:        
vermagic:       2.6.28-14-generic SMP mod_unload modversions 586 
parm:           debug:Turn on/off frontend debugging (default:off). (int)

---

### Post by ddrichardson on 2009-07-27
There are tda1004x, budget-core, budget-ci and dvb-core. Try them all:
```

SUSPEND_MODULES="tda1004x budget-core budget-ci dvb-core"
```
dvb-core is a good bet.  If reloading the module on resume isn't sufficient you will need to file a bug against the module.

---

### Post by jis on 2009-07-28
> **ddrichardson said:**
> 
```

SUSPEND_MODULES="tda1004x budget-core budget-ci dvb-core"
```


That worked :)

But is there something special about dvb-core?

---

### Post by jis on 2009-07-28
I tested that this was enough to make it work:
```
SUSPEND_MODULES="dvb-core"
```

I had to copy file dvb-fe-tda10045.fw to /lib/firmware/ to start with. I used a USB-connected DVB tuner before and I did not have to configure it manually.

---

### Post by ddrichardson on 2009-07-28
Is it working for you now then?

---

### Post by jis on 2009-07-28
Yes. Thanks for help.

---

### Post by ddrichardson on 2009-07-28
That's OK I was just checking :-)

---

