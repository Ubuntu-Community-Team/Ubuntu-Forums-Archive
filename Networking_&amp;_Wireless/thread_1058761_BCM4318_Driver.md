---
title: "BCM4318 Driver"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by lms5yc13 on 2009-02-03
Ok, so I have the infamous BCM4318 wireless card that doesn't work... At first, I could connect to the internet but then be kicked off shortly. My question is what is the correct driver I should be using? I tried the "bcm43xx-firmware" driver but I have to disable ndiswrapper ( I don't know how to do that). Also, I need a detailed process of what I should be doing because I'm pretty new to Ubuntu. Thanks.

---

### Post by Ayuthia on 2009-02-03
> **lms5yc13 said:**
> Ok, so I have the infamous BCM4318 wireless card that doesn't work... At first, I could connect to the internet but then be kicked off shortly. My question is what is the correct driver I should be using? I tried the "bcm43xx-firmware" driver but I have to disable ndiswrapper ( I don't know how to do that). Also, I need a detailed process of what I should be doing because I'm pretty new to Ubuntu. Thanks.

If you want to disable ndiswrapper, you will have to edit /etc/modules and remove ndiswrapper:
```
gksu gedit /etc/modules
```

Just to be safe, you can also blacklist ndiswrapper:
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
```

---

