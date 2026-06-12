---
title: "A wireless chipset that fully works with 8.10"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by xraynorm on 2008-12-18
Hello.

Is there any wireless chip sets that fully works out of the box with wpa encryption, with network manager with 8.10.

I have been reading through the forums and it seems most chipsets have problems.

The only chipset that seems 100% ok is the intel 2200 mini pci card. However installing this is a quite a big job with my laptop.

I currently have rt2500 based chipset, this will only work fully(full speed) when the network manager is bypassed. 

I would like to be able to switch between networks (Ethernet/wireless/mobile broadband) network manager seem to do this nicely.

Any recommendations?

---

### Post by joebeasley on 2008-12-19
The Airlink101 wireless PCI card works out of the box.  It uses a Realtek 8185 chipset.  

01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

---

### Post by wieman01 on 2008-12-19
My rt2570 has full speed with NM as of 8.10. Used to be a nightmare in previous versions.

---

### Post by xraynorm on 2008-12-19
Thanks for your replies

So the Realtek 8185 and rt2570 work fine with wpa and network manager?

---

### Post by wieman01 on 2008-12-19
> **xraynorm said:**
> Thanks for your replies

So the Realtek 8185 and rt2570 work fine with wpa and network manager?
The rt2570 does. Network Manager, WPA2 (AES), static IP addresses.

---

### Post by xraynorm on 2008-12-20
Thanks.

Is the rt2570 usb only? I cant seem to find a pcmcia model.

---

### Post by wieman01 on 2008-12-21
The rt2570 is a USB device. Yes.

---

### Post by xraynorm on 2008-12-22
Any pcmcia wireless card chipset recommendations?

---

