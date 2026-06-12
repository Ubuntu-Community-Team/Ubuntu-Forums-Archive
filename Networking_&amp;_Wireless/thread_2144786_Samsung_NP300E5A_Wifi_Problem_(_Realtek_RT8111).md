---
title: "Samsung NP300E5A Wifi Problem ( Realtek RT8111)"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by Bariseray on 2013-05-13
Hello Everyone,
I recently installed 13.04 from a usb and i have a  problem with my wifi. After 2-3 seconds of connecting to it i lose my  connection and i have to disable and reenable networking a couple of  time to get it work properly. Is this a driver issue ? What can i do to  fix this as a newbie. Any help is much appreciated...

---

### Post by IWantFroyo on 2013-05-13
To me it looks like Realtek RT8111 is a ethernet card.

Please run this and paste the output here.

```
lspci | grep 'Network'
```

---

### Post by Bariseray on 2013-05-13
Thanks for your quick reply, this is the result :
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)

---

### Post by IWantFroyo on 2013-05-13
Try plugging in an Ethernet cable and running "Additional Drivers".

Also, from a quick Google I get this thread:
[http://ubuntuforums.org/showthread.php?t=1941331](http://ubuntuforums.org/showthread.php?t=1941331)

It's rather old though, so be careful if you choose to implement anything.

---

### Post by Bariseray on 2013-05-13
Running additional drivers ?

---

### Post by IWantFroyo on 2013-05-13
It's an application. Open the dash and type "Additional Drivers", and then click on the icon of a motherboard.

---

### Post by Bariseray on 2013-05-15
It couldn't find any additional drivers.

---

