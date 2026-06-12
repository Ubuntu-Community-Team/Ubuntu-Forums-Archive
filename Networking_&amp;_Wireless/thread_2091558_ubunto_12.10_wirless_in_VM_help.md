---
title: "ubunto 12.10 wirless in VM help"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by matrixebiz on 2012-12-05
Hello, running ubuntu 12.10 in VM Player 5, wireless works VIA through my Windows 7 laptop but unable to actually see the adapter in ubuntu and other wireless networks. Please help me get ubuntu to install the proper driver and see my physical wireless card. I have a dell laptop with a DW1501 Wirless-N WLAN Half-Mini Card.

Thank you

---

### Post by chili555 on 2012-12-05
Please see: [http://communities.vmware.com/message/2097964](http://communities.vmware.com/message/2097964)> VMware Player always presents a wired NIC to the guest, no matter what the physical system uses. If you need a wireless adapter in the VM, you need to attach e.g. an USB wireless adapter to the host and connect it to the guest as an USB device.

---

### Post by CharlesA on 2012-12-05
Chili nailed it. The same is likely true for every other VM software. I know VBox does the same.

---

### Post by matrixebiz on 2012-12-05
Oh, ok, luckly I do have a USB network adaptor.

I'll try that and let you know if I need more help.

Thanks

---

