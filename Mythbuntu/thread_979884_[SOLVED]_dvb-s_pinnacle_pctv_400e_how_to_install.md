---
title: "[SOLVED] dvb-s pinnacle pctv 400e how to install?"
date: 2008-11-12
forum: Mythbuntu
---

### Post by freak42 on 2008-11-12
Hello all,

I am trying to install above satelite capture card on my mythbuntu 8.10 system. however I can't get it to work at all.

I extracted a .fw file that is supposedly needed for this box to work and installed it into /va/firmware/ .. the driver name is "dvb-usb-pctv-400e-01.fw

however I cannot access the box in mythbuntu setup. when I replug the box dmesg sais the following:

[  282.116156] usb 5-2: new high speed USB device using ehci_hcd and address 4
[  282.270226] usb 5-2: configuration #1 chosen from 1 choice

can someone point me in the right direction?

many thanks in advance

freak42

---

### Post by freak42 on 2008-11-13
* bump * ?

---

### Post by Rompalle on 2008-11-13
maybe this can help.

[http://ubuntuforums.org/showthread.php?p=4834676]("http://ubuntuforums.org/showthread.php?p=4834676")

---

### Post by freak42 on 2008-11-14
Hello,

thank you for your suggestion, I did install the v4l-dvb package (as described here: [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers))

however my card is still not recognized:

dmesg output upon pluggin in:
```
[  473.344134] usb 5-1: new high speed USB device using ehci_hcd and address 5
[  473.533129] usb 5-1: configuration #1 chosen from 1 choice

```

oh and I modprobe(d) following modules according to [http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_400e](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_400e) :

 - tda10086.ko
 - lnbp21.ko
 - tda826x.ko
 - dvb-usb.ko
 - dvb-usb-ttusb2.ko

So how do I get my card recognized?

---

### Post by freak42 on 2008-11-16
*bump*

I'd really appreciate somebody's help on this.

---

### Post by freak42 on 2008-11-30
bump? anybody? please?

---

### Post by freak42 on 2008-12-01
ok, just to let anybody know, that might be interested, it looks like my dvb-s receiver is defect and that is probably why it isn't correctly detected.

ah well what a shame and waste of time. :(

but thanks for reading anyhow

---

