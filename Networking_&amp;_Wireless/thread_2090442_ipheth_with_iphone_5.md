---
title: "ipheth with iphone 5"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by fennec62 on 2012-12-02
Hi

I try to use my iphone5 tethering with ubuntu 12.10
But ipheth don't know the iphone 5

i find a path 

```
linux-3.6.1/drivers/net/usb/ipheth.c	2012-10-07 10:41:28.000000000 -0500
+++ new/linux-3.6.1/drivers/net/usb/ipheth.c	2012-10-11 11:38:17.242000596 -0500
@@ -62,6 +62,8 @@
#define USB_PRODUCT_IPAD 0x129a
#define USB_PRODUCT_IPHONE_4_VZW 0x129c
#define USB_PRODUCT_IPHONE_4S	0x12a0
+#define USB_PRODUCT_IPHONE_5	0x12a8
+

#define IPHETH_USBINTF_CLASS 255
#define IPHETH_USBINTF_SUBCLASS 253
@@ -113,6 +115,10 @@
USB_VENDOR_APPLE, USB_PRODUCT_IPHONE_4S,
IPHETH_USBINTF_CLASS, IPHETH_USBINTF_SUBCLASS,
IPHETH_USBINTF_PROTO) },
+	{ USB_DEVICE_AND_INTERFACE_INFO(
+	 USB_VENDOR_APPLE, USB_PRODUCT_IPHONE_5,
+	 IPHETH_USBINTF_CLASS, IPHETH_USBINTF_SUBCLASS,
+	 IPHETH_USBINTF_PROTO) },
{ }
};
MODULE_DEVICE_TABLE(usb, ipheth_table);
```

But i can i do for aplly this patch 

thanks a lot

---

