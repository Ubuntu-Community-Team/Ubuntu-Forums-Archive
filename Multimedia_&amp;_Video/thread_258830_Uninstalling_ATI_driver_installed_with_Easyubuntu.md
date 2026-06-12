---
title: "Uninstalling ATI driver installed with Easyubuntu"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by finferflu on 2006-09-16
Hi all,

I was a bit unsure whether starting this thread here or in the section of third party projects, so I hope this is the right place.

I have recently given a look to Easyubuntu, not that I needed it, since I've been using Automatix, because I wantet to find something user-friendly enough to give to my unexperienced friends. Going thorugh the list, I've found a nice ATI driver and since I've got an ATI card I thought it would have been a good thing to install. My card was actually working before I had installed the driver, and now, when I try to play 3D games (i.e. Sauerbraten), I can hardly move around.

This is my ATI card:

```
$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
```

Is there any way I can get back to the default Ubuntu configuration, or uninstall that driver I've installed?


Thanks for your time.

---

### Post by metalqga on 2006-09-16
```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver

```
[http://doc.gwos.org/index.php/Uninstall_ATI_driver]("http://doc.gwos.org/index.php/Uninstall_ATI_driver")

---

### Post by finferflu on 2006-09-16
Thanks a lot, it works again now!

I just needed to uninstall the xorg-driver-fglrx.

Thanks!

---

