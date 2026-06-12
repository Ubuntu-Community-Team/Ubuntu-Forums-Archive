---
title: "Wireless problems"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by spectra1 on 2006-01-06
I have a Linksys WMP54GS Wireless G card. Can anyone tell me if Ubuntu supports this card and if so how do I get the OS to recognize the card. When I install Ubuntu is says that there is no network card

---

### Post by healychan on 2006-01-06
According to the NdisWrapper list. Your card should work fine with Ubuntu.
Here is what I find in the NdisWrapper list
```
Card: Linksys #[WMP54GS] Wireless-G PCI Adapter with Speedbooster -- [link here|List#WMP54GS]

    * Chipset: Broadcom Corporation BCM94306 802.11g (rev 03)
    * pciid: 14e4:4320
    * Driver: Linksys ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe (new version)
    * Other: Ndiswrapper 0.11 and 0.12. Works fine with 64-bit WEP key and WPA supplicant (Fedora core-2, Kernel 2.6.8 and 2.6.9). Use WMP54GS.inf 
```

what you need to do is install the ndiswrapper package. This package enable you to use Windows drivers on Ubuntu. 

Once you installed the ndiswrapper, follow this HOWTO [https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

I hope it helps. :p

---

### Post by Rob2687 on 2006-01-06
It works fine for me. You have to set it up after you install Ubuntu.

---

