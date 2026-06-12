---
title: "Atheros PCI changing model number w/ Karmic"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by Cuba71 on 2009-11-16
This is how Karmic and Jaunty differ when identifying the Atheros wireless PCI adapter in my Toshiba laptop A135-S4527

This is when running Jaunty 9.04

```


user@ubuntu:~$ lspci -nn | grep Atheros
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
```

and this is when running Karmic 9.10 from the LiveDVD.  Both version use the same driver "ath5k"

```

user@ubuntu:~$ lspci -nn | grep Atheros
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

```

The adapter model number changes from AR242x to AR5001.  Both versions use the same driver "ath5k"

Any clues anyone ???

---

### Post by puppywhacker on 2009-11-16
lspci only gets the vendor and product numbers and shows the name it finds for that combination in the file /usr/share/misc/pci.ids 

```
168c  Atheros Communications Inc.
        001c  AR5001 Wireless Network Adapter
```

Ubunutu uses a a version from [http://pciids.sourceforge.net/](http://pciids.sourceforge.net/)

For USB the same applies, the file is /usr/share/misc/usb.ids and the website with up to date ids is [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)

---

### Post by Cuba71 on 2009-11-16
Thank you

---

