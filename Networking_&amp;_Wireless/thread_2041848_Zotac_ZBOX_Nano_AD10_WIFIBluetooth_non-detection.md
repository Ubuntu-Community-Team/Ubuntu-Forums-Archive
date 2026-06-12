---
title: "Zotac ZBOX Nano AD10 WIFI/Bluetooth non-detection"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by num3thod on 2012-08-13
I've recently bought this ZBOX Nano AD10, which has a WIFI/Bluetooth combo adapter. When installing Ubuntu 12.04 (32 or 64), it does not recognize either WIFI or Bluetooth.

The thing is, I have searched and searched but cannot figure out the make or model for this particular adapter.

Can anybody shed some light as to how I may fix this problem?

Many thanks,

MR

---

### Post by sankeytm on 2012-08-14
I spoke with somebody else who bought an AD10 a long time ago, and he says his AD10 uses Atheros wifi, while the current revision uses this Ralink:
[http://www.ralinktech.com/en/02_products/product.php?sn=1036](http://www.ralinktech.com/en/02_products/product.php?sn=1036)

Linux driver available at Zotac website:
[http://www.zotac.com/components/gpd_download/Download/count.php?var=1763&driverlink=http://downloads.zotac.com/mediadrivers/mb/download/NB087_WiFi_V2600_20120508.tar.gz](http://www.zotac.com/components/gpd_download/Download/count.php?var=1763&driverlink=http://downloads.zotac.com/mediadrivers/mb/download/NB087_WiFi_V2600_20120508.tar.gz)
But that "only supports wifi", not bluetooth.

Here is another one I found:
[http://www.driversdown.com/drivers.asp?ID=124669&brNum=3&show=0](http://www.driversdown.com/drivers.asp?ID=124669&brNum=3&show=0)

It is a kernel module that needs to be built and loaded. Ideally it should somehow be included upstream so all distributions can have it too.
This explains why people that bought their AD10 3+ months ago seem to have no problems, while new buyers can't get WIFI to work.

---

