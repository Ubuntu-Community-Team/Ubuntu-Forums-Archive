---
title: "Wireless no longer working - kind of new to Ubuntu"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by dmwilson220 on 2011-09-08
Hi all, I have a HP DV4 2040us. I've had issues with my wifi since the get go where the wireless connection would essentially cut out at random. I thought that the issue would be the driver so used the ndiswrapper tool in the software center to install the driver for my card (Atheros AR298x). After a reboot, I can longer access wireless, so unless I can get a fix, my laptop is grounded to wired internet.

Any help is appreciated, thanks.

EDIT- Update:

So I've uninstalled the windows driver, now its not showing any wireless card what so ever. Anyone know how I can just reinstall the Ubnutu drivers?

---

### Post by dmwilson220 on 2011-09-09
Bump.

I've gotten wireless working again by using

   sudo modprobe -a ath9k

That allows me to turn on the original wireless driver. Now does anyone know of a way to make it stick? The only issue I'm still running into is I have to use that code on every boot, is there a way to have it so it starts on boot?

---

### Post by wildmanne39 on 2011-09-09
Hi, you need to make sure you completely removed ndiswrapper or you will have issues with connectivity.

This will make it load at boot up.
```
sudo su 
echo ath9k >> /etc/modules 
exit
```
Thank you

---

### Post by dmwilson220 on 2011-09-09
> **wildmanne39 said:**
> Hi, you need to make sure you completely removed ndiswrapper or you will have issues with connectivity.

This will make it load at boot up.
```
sudo su 
echo ath9k >> /etc/modules 
exit
```
Thank you

Hi, and thanks, all I would need to do to remove ndiswrapper is to 

```
 sudo apt-get remove 
```

for each of the ndiswrapper files right?

---

### Post by wildmanne39 on 2011-09-09
Hi, this is how to remove ndiswrapper if any part of it is still there.
```
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
run the commands one at a time.

If I have helped you in a small way would you show your support for my ubuntu membership by clicking on ubuntu membership in my signature?

Would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by dmwilson220 on 2011-09-09
Done and done, thanks again for your help. Running nothing but Ubuntu on my laptop is a bit different than wubi, but I'm enjoying it so far, just have a lot to learn, that's all.

Thanks again.

---

### Post by wildmanne39 on 2011-09-09
Hi, your welcome! and thank you enjoy ubuntu, if you need more help post in the right section of the forum and most always your issue will be resolved.
Thank you

---

