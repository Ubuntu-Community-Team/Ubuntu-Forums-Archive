---
title: "Trust WB-1400T webcam"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by perce on 2007-12-23
I have a Trust WB-1400T USB webcam. When I plug it, it is recognised as a Pixart PAC207-BCA and the module gspca is loaded. However I only see colour shadows from 
it. The output of dmesg is:

```

[104907.300000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[104907.532000] usb 2-1: configuration #1 chosen from 1 choice
[104907.536000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. (PAC207)
[105266.164000] usb 2-1: USB disconnect, address 6
[105305.764000] usb 2-1: new full speed USB device using uhci_hcd and address 7
[105305.996000] usb 2-1: configuration #1 chosen from 1 choice
[105306.000000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. (PAC207)
paolo@Bach:~/Domande/Estero2007/Imperial$ lsmod |grep gspca
gspca                 608336  1 
videodev               29312  2 gspca
usbcore               138632  9 gspca,usb_storage,libusual,usblp,usbhid,hci_usb,ehci_hcd,uhci_hcd

```

Can anybody help, please?

---

### Post by perce on 2008-01-03
bump

---

