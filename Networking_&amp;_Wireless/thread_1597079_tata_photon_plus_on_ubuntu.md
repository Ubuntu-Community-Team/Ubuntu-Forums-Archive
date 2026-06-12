---
title: "tata photon plus on ubuntu"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by netloglinux on 2010-10-14
Hi,
My mobile broadband device is "Huawei EC1261 HSIA USB stick" I tried almost all solutions posted over net to configure my usb broadband but it doesn't work. I found the model number of my device doesnt match to any of the previous quoted models. whenever i plug the usb device it gets recognized as CD drive and a storage device in windows. kindly help me how to configure this on ubuntu 10.04.

the vendor and product id are 12d1 and 1446 (not 140b).

thanks in advance..

---

### Post by pdc on 2010-10-15
you are likely to need usb_modeswitch

download the .deb version from the debian repository

AND the data file; it should "flip" your device and enable it to be seen as a modem

---

### Post by netloglinux on 2010-10-15
Thanks for the info mate.. i have both usb_modeswitch and data, can you kindly guide me how to flip the device... just started using ubuntu so my knowledge is zero about the controls and environment..

---

