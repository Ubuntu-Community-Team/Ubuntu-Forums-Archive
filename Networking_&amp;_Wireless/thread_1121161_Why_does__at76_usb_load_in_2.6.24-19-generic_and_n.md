---
title: "Why does  at76_usb load in 2.6.24-19-generic and not in 2.6.27-11-generic"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by havensrobert on 2009-04-09
seeing if i can try this another way....

my Linksys WUSB11 V2.6 802.11b Adapter works fine in 2.6.24-19-generic and not at all in 2.6.27-11-generic.  It's clear to me that the at76_usb driver loads in 2.6.24 and not in 2.6.27.  I've tried to install the at76c503a-cvs driver and that didn't work (either was installed properly or failed to load) and i tried the atmelwlandriver-3.4.1.1 as well and either failed to install it properly or it's not loading.  I'm at a loss.  Could it be the firmware of the adapter?  Could it be that i need to blacklist something in 2.6.27?  why does the below happen when booting in 2.6.24 and only the uhci_hcd in 2.6.27?



61.257153] usbcore: registered new interface driver at76_usb
[   62.513921] loop: module loaded
[   62.566865] lp0: using parport0 (interrupt-driven).
[   62.857363] Adding 546168k swap on /dev/sda5.  Priority:-1 extents:1 across:546168k
[   63.497130] usb 1-2.3: reset full speed USB device using uhci_hcd and address 4
[   63.604086] usb 1-2.3: device firmware changed
[   63.607034] usb 1-2.3: USB disconnect, address 4
[   63.607184] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/wireless/at76/at76c503.c: wlan0 disconnecting
[   63.607217] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/wireless/at76/at76c503.c: at76_usb disconnected
[   63.681000] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
[   63.797284] usb 1-2.3: configuration #1 chosen from 1 choice
[   63.933764] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/wireless/at76/at76c503.c: firmware version 1.101.4 #84 (fcs_len 4)
[   63.934772] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/wireless/at76/at76c503.c: device's MAC 00:06:25:48:01:4e, regulatory domain FCC (U.S) (id 16)
[   63.935935] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/wireless/at76/at76c503.c: registered wlan0
[   66.211484] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/wireless/at76/at76c503.c: 2522: assertion dev->istate == INIT failed
[   67.698769] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL failed
[   


oh and i tried ndiswrapper and that didn't work either (again may not have done it right but i think i did what the many instructions out there say)

I don't get it....HELP!

Thanks,

=rjh

---

