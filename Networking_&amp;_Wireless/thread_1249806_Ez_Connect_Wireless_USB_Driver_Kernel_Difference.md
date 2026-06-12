---
title: "Ez Connect Wireless USB Driver Kernel Difference"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by Rashedul on 2009-08-25
I recently upgraded one of the family computer to Jaunty from Intrepid. The wireless USB adapter was working before the upgrade and stopped working with the new Kernel. I'm running Jaunty now but I can't run it with the latest Kernel and still make it work. So from Grub menu I'm selecting the previous kernel to make my USB wireless driver work. 
So instead of kernel 2.6.28-15-generic I'm running kernel 2.6.27-9-generic.

I'm assuming the new kernel got rid of driver support for my wireless adapter. If that is the case how do I patch the new kernel so I can still run the latest kernel that ships with Jaunty instead of relying on running jaunty with an older kernel? 

```
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0707 Standard Microsystems Corp.
  idProduct          0xee13 EZ-Connect 802.11g Adapter
  bcdDevice           10.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1

```

---

### Post by Rashedul on 2009-08-28
any ideas?

---

