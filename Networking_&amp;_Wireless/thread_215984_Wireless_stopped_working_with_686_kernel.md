---
title: "Wireless stopped working with 686 kernel"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by oobnuker on 2006-07-14
Hey - on my Acer 5672, when I switched to the 686 kernel to use dual core, I lost the ability to use my wireless. If I switch back to the 386, it works fine.

This is probably an easy one, but I couldn't find anything when I searched.

Any ideas?

Thanks.

---

### Post by infoburner on 2006-07-14
the problem is probably that you dont have the driver for the new kernel. try  going into synaptic and re-install whatever wireless card driver you are using.

---

### Post by filiphw on 2006-07-15
For me too... how do u reinstall the driver... that was installed during installation for me... can't find it in package manager... 

Netgear PCI card:
AR5212 802.11abg NIC
Linux drv: ath_pci
/org/freedesktop/Hal/devices/pci_8086_244e

---

### Post by infoburner on 2006-07-15
> **filiphw said:**
> For me too... how do u reinstall the driver... that was installed during installation for me... can't find it in package manager... 

Netgear PCI card:
AR5212 802.11abg NIC
Linux drv: ath_pci
/org/freedesktop/Hal/devices/pci_8086_244e

```

sudo apt-get install linux-restricted-modules-`uname -r`

```

this will install the madwifi driver which is for atheros chipset based cards like the one you are using

---

### Post by oobnuker on 2006-07-15
Someone figured it out in another thread. The trick is the latest kernel update does not appear to have a corresponding restricted-modules package. If you select the previous 686 kernel to boot, wireless works and so do both cores. So I guess we have to wait for the latest restricted modules.

---

