---
title: "usb wifi adapter frustration"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by theflayindutchmn on 2010-05-28
greetings,

So I started yesterday off wanting to install this USB wifi adapter on my PC (which is mini-itx so has additional pci slots)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166041](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166041)
[http://www.rosewill.com/products/1280/productDetail.htm](http://www.rosewill.com/products/1280/productDetail.htm)

it has the Ralink 3070 chipset. I tried everything I found when googling, nothing came close to working, this was in Fedora12. So I gave up and installed Ununtu 10.04, hoping for better luck there.

Ubuntu will recognise the presence of a wifi adapter, here's the output from iwconfig


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

But it sees no wifi networks and generally won't do anything; I don't think it has the right driver.

Rosewill does list a (linux) driver and so does Ralink, but again, neither of these come close to working.

has anyone gotten this adapter or chipset to work in ubuntu? Or otherwise, can anyone recommend me a usb wif adapter that just works out of the box, with no problems. I'm tired of spending time on this.

On the upside, 10.04 feels really nice.

thanks in advance,
-nick

---

### Post by chili555 on 2010-05-28
Please open a terminal and post:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -i RT2
lsusb
```Thanks.

---

### Post by theflayindutchmn on 2010-05-28
Thanks for the reply.

```

nick@portable:~$ lsmod | grep -e rt2 -e rt3
rt2870sta             525366  0 
rt2800usb              33496  0 
rt2x00usb              11260  1 rt2800usb
rt2x00lib              32133  2 rt2800usb,rt2x00usb
led_class               3732  1 rt2x00lib
mac80211              238128  2 rt2x00usb,rt2x00lib
cfg80211              148386  2 rt2x00lib,mac80211
crc_ccitt               1675  1 rt2800usb
nick@portable:~$ dmesg | grep -i RT2
[   15.340569] Registered led device: rt2800usb-phy0::radio
[   15.340576] Registered led device: rt2800usb-phy0::assoc
[   15.340583] Registered led device: rt2800usb-phy0::quality
[   15.340910] usbcore: registered new interface driver rt2800usb
[   15.341261] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.343763] usbcore: registered new interface driver rt2870
[   16.986870] rt2800usb 1-1.3:1.0: firmware: requesting rt2870.bin
nick@portable:~$ lsusb
Bus 002 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 003: ID 04d9:0702 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
nick@portable:~$ 

```


thanks again,
-nick

---

### Post by chili555 on 2010-05-28
Please see here at post #11. You have too many drivers loading and the solution is the same.

[http://ubuntuforums.org/showthread.php?t=1444925&highlight=rt2800usb&page=2](http://ubuntuforums.org/showthread.php?t=1444925&highlight=rt2800usb&page=2)

---

### Post by theflayindutchmn on 2010-05-29
Yep, that did it. thanks very much for your help.

-nick

---

