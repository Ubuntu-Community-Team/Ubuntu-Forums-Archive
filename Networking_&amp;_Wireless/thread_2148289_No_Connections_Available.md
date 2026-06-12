---
title: "No Connections Available"
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by chainsaw721 on 2013-05-24
Hi all,
       Have very recently installed Ubuntu 12.04.2 on an old laptop, replacing Vista. This is only my second installation of Ubuntu, and my previous install on my desktop I never actually encountered any problems, so I'm not really the greatest troubleshooter nor do I possess the greatest knowledge about any of this. Basically, during installation, I had a wired connection that was working, so during install, all updates were able to download and everything seemed in place. Wasn't able to get the wireless to connect though, that's why I had to go wired. Upon reboot after install, I'm not able to get any connections, wired or wireless. I have read around many forums so far and poked at everything that i could make sense of, but nothing seems to have worked. I don't really care about the wired connection, because it is a laptop and will be very rarely if ever have a wired connection. The Network Manager says there are No Network Devices Available, so something must just be turned off somewhere. Any help in getting things going is much appreciated!

Dell Inspiron 1501
Broadcom BCM 4311 802.11b/g WLAN (Rev 01)
Broadcom BCM 4401-B0 100Base-TX (Rev 02)

I don't know what kind of other info anyone might want for troubleshooting, but ask and you shall receive!
Thanks!

---

### Post by Hadaka on 2013-05-24
Hi, please open a terminal ctrl/alt/t
then Copy and paste the following..
one line at a time
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
is it working??

---

### Post by praseodym on 2013-05-24
Without any connection, install this file:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

---

### Post by chainsaw721 on 2013-05-25
Thanks a ton guys, helped me out big time! Worked like a charm! After running Hadaka's lines i got a wired connection running finally, and then installing Praseodym's file there got the wireless going. Thanks again guys, much appreciated!

---

### Post by Albatros91 on 2013-05-25
> **Hadaka said:**
> Hi, please open a terminal ctrl/alt/t
then Copy and paste the following..
one line at a time
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
is it working??

Hello.
I have installed the bcmwl-kernel-source, but I am not able to connect to the wlan, it tries it and cannot establish a connection. I tried your lines but it still not work.
I have a fresh installed ubuntu 13.04 64-bit and the network controller is BCM4313.

Do you or anyone other have a idea?
I try now since above 10 hours to get the wlan working. If you need any infos I will post them.

Thanks,
Albatros

---

### Post by praseodym on 2013-05-25
Hi Albatros,

uninstall the STA driver and install the firmware according to this
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```

---

