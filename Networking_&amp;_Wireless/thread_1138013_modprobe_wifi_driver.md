---
title: "modprobe wifi driver"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by tech_cheetah on 2009-04-26
Everytime I log into ubuntu, I have to run following command only then ubuntu connects to wifi:
```
sudo modprobe iwl3945
```

Is there any way to make it automatic while starting ubuntu ?

---

### Post by Svensk023 on 2009-04-26
I believe you can add iwl3945 to your 

/etc/modules

so it will load at boot.

---

