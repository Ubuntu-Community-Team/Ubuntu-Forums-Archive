---
title: "Problem with USB 3G Dongle"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by richie60 on 2010-12-19
Hi, I have a laptop dual booting Windows 7 & Ubuntu 10.04.  If I boot straight into Linux & try to connect with the USB dongle, it's not there in Network Manager, however if I first boot into Windows, connect the dongle then disconnect & shutdown to reboot into Linux, the dongle is instantly recognised & works no problem.

My question is, how can this be?  How can one OS have an effect on the other?  Is there something that remains in RAM that makes the dongle work in Linux?

---

### Post by alexfish on 2010-12-19
hi

may be the modem stops in the switched state IE cd or mass-torage is disabled , as power to the device
is still  on ; only an assumption

Have you installed usb_modeswitch , via synaptic package manager

or the latest version from here

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

use the link to debian site / don't forget to download both packages : modeswitch and modeswitch data

alexfish

---

