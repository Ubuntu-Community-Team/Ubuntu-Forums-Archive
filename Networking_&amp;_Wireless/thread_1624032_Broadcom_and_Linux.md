---
title: "Broadcom and Linux"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by PuddingKnife on 2010-11-17
Does anyone know how to use the newly opened Broadcom wireless drivers?

Article:
[http://www.phoronix.com/scan.php?page=news_item&px=ODU4Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODU4Mg)

I have a netbook running 10.10 that can't connect via ethernet OR wireless, so this would be really helpful!

---

### Post by corncob on 2010-11-17
> **PuddingKnife said:**
> Does anyone know how to use the newly opened Broadcom wireless drivers?

Article:
[http://www.phoronix.com/scan.php?page=news_item&px=ODU4Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODU4Mg)

I have a netbook running 10.10 that can't connect via ethernet OR wireless, so this would be really helpful!

I'm not familiar with that article/site but my HP Pavilion has a Broadcom BCM4312 which I got working by installing bcmwl-kernel-source:

```
sudo apt-get install bcmwl-kernel-source
```

You can also install it from System > Administration > Synaptic Package Manager.  Hope it works for you.

---

### Post by PuddingKnife on 2010-11-17
You can do that w/o an internet connection?

---

### Post by corncob on 2010-11-17
> **corncob said:**
> 
```
sudo apt-get install bcmwl-kernel-source
```


I should have mentioned I got errors during the install but, nonetheless, the wifi started working.

---

### Post by cariboo on 2010-11-17
If you have a cd-rom drive you can install the Broadcom drivers from the Live CD, if you are using a usb thumb drive, mount it to /cdrom, and make sure it is enabled in Software Sources.

---

### Post by corncob on 2010-11-17
> **PuddingKnife said:**
> You can do that w/o an internet connection?

I guess you can't.  I was thinking of my own case where the wired connection was working.

---

### Post by PuddingKnife on 2010-11-17
> **cariboo907 said:**
> If you have a cd-rom drive you can install the Broadcom drivers from the Live CD, if you are using a usb thumb drive, mount it to /cdrom, and make sure it is enabled in Software Sources.

Ok, this seems like the most doable path for me. Is there a guide somewhere you can direct me to to mount the USB to /cdrom? I am not fluent in BASHese  ;)

---

