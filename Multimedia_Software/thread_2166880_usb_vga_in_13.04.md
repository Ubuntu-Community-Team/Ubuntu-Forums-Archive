---
title: "usb vga in 13.04?"
date: 2013-08-11
forum: Multimedia Software
---

### Post by jarush on 2013-08-11
I've got a jCreate JUA350 that allows me to connect an additional display via USB.  

It looks like the display adapter is being recognized by the kernel but I get some odd error messages in dmesg.  Anyone know how to fix?

```

[87698.889581] usb 3-1: new SuperSpeed USB device number 4 using xhci_hcd
[87698.906799] usb 3-1: Parent hub missing LPM exit latency info.  Power management will be impacted.
[87698.909794] usb 3-1: New USB device found, idVendor=0711, idProduct=5800
[87698.909807] usb 3-1: New USB device strings: Mfr=1, Product=9, SerialNumber=0
[87698.909813] usb 3-1: Product: MCT USB3.0 External Graphics Device (HDMI)
[87698.909818] usb 3-1: Manufacturer: MCT Corp.
[87699.911978] 4:2:1: cannot get freq at ep 0x85
[87700.914411] 4:3:1: cannot get freq at ep 0x6
[87701.980849] 4:2:1: cannot get freq at ep 0x85
[87702.979221] 4:2:1: cannot set freq 48000 to ep 0x85
[87704.033752] 4:2:1: cannot get freq at ep 0x85
[87705.032312] 4:2:1: cannot get freq at ep 0x85
[87706.046844] 4:3:1: cannot get freq at ep 0x6
[87707.045097] 4:3:1: cannot set freq 48000 to ep 0x6
[87717.035733] 4:3:1: usb_set_interface failed (-110)
[87722.028470] 4:3:1: usb_set_interface failed (-110)
[87727.020908] 4:3:1: usb_set_interface failed (-110)
[87732.013678] 4:3:1: usb_set_interface failed (-110)
[87737.010013] 4:3:1: usb_set_interface failed (-110)
[87742.006680] 4:3:1: usb_set_interface failed (-110)
[87746.999277] 4:3:1: usb_set_interface failed (-110)


```

---

