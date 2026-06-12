---
title: "Netgear WNA1000 working in Lucid"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by Slave2Metal on 2010-05-30
Using the latest compat wireless [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

In my instance, compat-wireless-2010-5-29
 
after installing, which will take some time
```
sudo modprobe ar9170usb
```May have to add ar9170usb to modules list so it loads on boot.  These steps may not be perfect for everyone.  This is just what I did to get this adapter to work with kernel 2.6.32-22.  Make sure there isn't a windows driver installed if you have tried using ndiswrapper.  Although, I did have arusb_xp installed via ndis and after installing the compat drivers, I got nothing.  Then ```
ndiswrapper -l
``` showed arusb_xp was present, but also showed ar9170usb as an alternate driver.  So I was missing the last piece to get it going and that was the code above.  After sudo modprobe ar9170usb, networks were picked up instantly.  Hopefully this will help someone, even though it's a jumbled mess.

Also, the adapter connects using PSK WPA2 Personal
You will need to recompile the driver if the linux image or kernel changes.

---

