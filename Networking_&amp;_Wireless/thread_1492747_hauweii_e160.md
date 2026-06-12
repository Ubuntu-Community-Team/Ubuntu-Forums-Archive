---
title: "hauweii e160"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by fysiker on 2010-05-25
hi everyone...

does anyone of you use a hauweii e160 usb mobile broadband connection?  in ubuntu 9.10 it worked, but now (10.04), after the remove of  /proc/bus/usbfs it wont't get recogniced as an internet-device.

how should i handle this problem?

kind reguards

ps [have a look at here]("http://ubuntuforums.org/showthread.php?t=1486627")
why should i make a symlink from kernel/**debug** to /proc/bus/usb/devices

---

### Post by labinnsw on 2010-05-26
Check if wvdial is installed. If not,
1.  Install it, (hopefully, you have some alternate internet connection) 
2.  Disconnect any internet connection. 
3.  Unplug then plug in your USB modem.
After a short while, you should have connection.

---

### Post by pdc on 2010-05-27
Hi fysiker

> *how should i handle this problem*?

> **in ubuntu 9.10 it worked**,

? go back to 9.10?

---

### Post by shebaw on 2010-05-27
No you shouldn't go back to Ubuntu 9.10. I had similar problem, my Huwaei EC1261 worked in Ubuntu 9.10 but didn't work on Ubuntu 10.04. Installing usb-modswitch from synaptic fixed the problem and I'm using it to connect to the internet.
Hope this helps.

---

