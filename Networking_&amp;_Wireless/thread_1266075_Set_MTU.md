---
title: "Set MTU?"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by JakP on 2009-09-14
Does anyone know if you can alter MTU using terminal?  Using wicd and it doesn't seem to have a way to set this manually

Thanks

---

### Post by chili555 on 2009-09-14
```
sudo ifconfig wlan0 mtu 1400
```If you want to make it permanent, add it to */etc/rc.local* like this:```
# By default this script does nothing.

ifconfig wlan0 mtu 1400

exit 0

```Obviously, substitute your details here.

---

### Post by JakP on 2009-09-14
Awesome, many thanks

---

