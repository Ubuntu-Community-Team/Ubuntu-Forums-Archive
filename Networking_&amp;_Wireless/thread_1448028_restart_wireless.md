---
title: "restart wireless?"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by pycoed on 2010-04-06
When my wireless connection drops, which is often!, the only way to reconnect it is to reboot (Dell Inspiron 1150 with Xubuntu 9.10). Is there any way I can restart the wireless services or otherwise achieve thsi without closing down & rebooting? I have tried the obvious of disable & re-enable wireless connections & networking to no avail. Also "sudo /etc/init.d/networking restart" didn't do it either.

---

### Post by chili555 on 2010-04-06
Please try:```
sudo ifconfig wlan0 down && sudo ifconfig wlan0 up
```Substitute your wireless interface, if it's not wlan0.

---

### Post by pycoed on 2010-04-06
> **chili555 said:**
> Please try:```
sudo ifconfig wlan0 down && sudo ifconfig wlan0 up
```Substitute your wireless interface, if it's not wlan0.

Thanks for the response, but no joy. If I reboot, all is fine until the connection drops ( 10 mins up to perhaps a couple of hours), but then I need to reboot. Any other ideas?

Cheers

---

