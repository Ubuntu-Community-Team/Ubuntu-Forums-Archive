---
title: "Broadcom bcm4312 with RT kernel"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by beefbonanza on 2012-01-18
hi everybody,
sorry for reposting this topic but I think maybe this forum is the more appropriate place....
I recently installed the realtime kernel according to this manual
[http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel](http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel)
used the version given there... although there seem to be newer ones
I also installed some Ubuntu Studio packages, namely
ubuntustudio-desktop
ubuntustudio-audio
ubuntustudio-audio-plugins

Now, my WiFi-module (Broadcom BCM4312 on a Dell Vostro 1310) doesn't  work anymore. I was using the proprietary Broadcom Driver before,  when I'm now trying to re-activate it  in the additional drivers menu (as the is driver  listed NOT activated) it fails, logging the following to  /var/log/jockey.log:
```

2012-01-17 22:26:37,823 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-01-17 22:26:37,930 DEBUG: BroadcomWLHandler enabled(): kmod  disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```

any ideas how i can get the card working? doesn't need to be in RT but after trying no it's also not working anymore in the generic kernel...

thanks in advance

---

### Post by praseodym on 2012-01-18
From Ubuntu 11.04 on you can use the b43 driver as well, but you need to download the firmware for it via cable (if possible). Deactivate it first, and

```
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
wget [http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz](http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz) 
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/
```

---

