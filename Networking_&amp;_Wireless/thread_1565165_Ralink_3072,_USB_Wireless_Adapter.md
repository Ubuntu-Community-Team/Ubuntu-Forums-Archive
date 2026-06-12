---
title: "Ralink 3072, USB Wireless Adapter"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by tew88 on 2010-08-31
I've just attempted to install the following product: [http://www.tenda.cn/product/show.php?productid-349.html](http://www.tenda.cn/product/show.php?productid-349.html).

**lsusb** lists it as:
```
Bus 002 Device 002: ID 148f:3072 Ralink Technology, Corp.
```

After plugging it in, **iwconfig** showed:
```
no wireless extensions.
```

I was advised to, and did, compile compat-wireless. Since doing this, **iwconfig** now shows this:

```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

However, the adapter still does not work. It has been suggested to me that it is a firmware issue, and **dmesg** seems to confirm this:

```
[   12.267067] phy0 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset.
[   12.337226] phy0 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset.
```

Can anyone suggest how I may be able to remedy this so that I can connect to wireless networks?

I'm inexperienced with Linux, so please don't assume any knowledge!

Thanks,

Tom.

---

### Post by chili555 on 2010-08-31
The problem may actually be that this device is claimed by two different drivers that conflict. Let's do some diagnostics and see what's happening. Please post:```
dmesg | grep -e rt2 -e rt3
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by Renagade on 2011-06-18
I'm having pretty much exactly the same issue, I don't know if you can help, but
1) I -JUST- updated to 11.04 (it worked in 10)
2) The dongle still works in Win 7 
3) I'm LOST! :-(

Device:
[http://www.tenda.cn/tendacn/product/show.aspx?productid=365](http://www.tenda.cn/tendacn/product/show.aspx?productid=365)

```
dan@DRAGON:~$ lsusb
...
Bus 002 Device 012: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter

``````
dan@DRAGON:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

``````
dan@DRAGON:~$ dmesg | grep -e rt2 -e rt3
[    8.890182] Registered led device: rt2800usb-phy0::radio
[    8.890206] Registered led device: rt2800usb-phy0::assoc
[    8.890226] Registered led device: rt2800usb-phy0::quality
[    8.890561] usbcore: registered new interface driver rt2800usb
[    9.725409] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.729043] usbcore: registered new interface driver rt2870
[   14.454411] phy0 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset.
[ 1627.925436] Registered led device: rt2800usb-phy1::radio
[ 1627.925457] Registered led device: rt2800usb-phy1::assoc
[ 1627.925473] Registered led device: rt2800usb-phy1::quality
[ 1628.039060] phy1 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset.
dan@DRAGON:~$ lsmod | grep -e rt2 -e rt3
rt2870sta             450556  0 
rt2800usb              18235  0 
rt2800lib              45181  1 rt2800usb
crc_ccitt              12667  2 rt2870sta,rt2800lib
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              294370  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211
dan@DRAGON:~$
```

---

### Post by Renagade on 2011-06-23
Figured it out!
Easiest and simplest solution:
[http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working](http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working)

:-)

---

