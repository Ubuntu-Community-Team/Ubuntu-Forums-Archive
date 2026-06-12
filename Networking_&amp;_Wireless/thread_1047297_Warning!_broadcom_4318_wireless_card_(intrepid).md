---
title: "Warning! broadcom 4318 wireless card (intrepid)"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by acimmarusti on 2009-01-22
I warn you not to use the latest drivers from b43 linux, which is what happens if you do this:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

I got this card working fine using the older broadcom drivers. I used a deb package originally meant for hardy (ubuntu 8.04) found here (b43-firmware):

[http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)

Once you use it you must restart. It works well in intrepid too. But be advised NOT to use the deb package present in that website, but meant for intrepid, because it contains the latest drivers and causes the wireless to behave abnormally and won't connect to networks at times.

If you need any help, just contact me. You don't need "no stinking" ndiswrapper hehe

---

### Post by lms5yc13 on 2009-02-02
Ok, So I downloaded the bcm43xx firmware driver but it says in terminal that I need to disable ndiswrapper. It tells me that I need to type in the command : sudo ndiswrapper -l. - that doesn't work, so how am I supposed to get it to work?

---

### Post by acimmarusti on 2009-02-03
Hi,

This works if you don't have ndiswrapper already working for you. Unfortunately I can't help you here, as I have never used it. However, I guess you could try removing the ndiswrapper package entirely from your system. If you get dependency problems, then I suggest you don't do it.

Andres

---

### Post by mathp on 2009-05-03
> **acimmarusti said:**
> I warn you not to use the latest drivers from b43 linux, which is what happens if you do this:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

I got this card working fine using the older broadcom drivers. I used a deb package originally meant for hardy (ubuntu 8.04) found here (b43-firmware):

[http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)

Once you use it you must restart. It works well in intrepid too. But be advised NOT to use the deb package present in that website, but meant for intrepid, because it contains the latest drivers and causes the wireless to behave abnormally and won't connect to networks at times.

If you need any help, just contact me. You don't need "no stinking" ndiswrapper hehe




Hey !

Just wanted to thank you. I'm quite new with Ubuntu and I f*cked around for 3-4 hours befor I finally found your thread and tried it. It's working perfectly.

cheers !

---

### Post by acimmarusti on 2009-05-04
Actually I've found the new firmware works (the older one, sometimes causes kernel freezes). However, to install it, requires a little bit more work:

The package b43-fwcutter in the ubuntu repositories must be installed. It's not installed by default, so if you only rely on your wireless for internet what you should do is pre-download it from here: [http://packages.ubuntu.com/search?searchon=sourcenames&keywords=b43-fwcutter](http://packages.ubuntu.com/search?searchon=sourcenames&keywords=b43-fwcutter) (depending on your version)

Install it by double clicking or with the terminal command (*dpkg -i <package name>*). It will ask you to fetch the firmware for you, this is perfect if you already have a working LAN internet connection, but if you do not, you should refuse.

The firmware must also be downloaded manually in advance, if you don't have a working internet connection. Here: [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Then, do this:

```

export FIRMWARE_INSTALL_DIR="/lib/firmware"
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

```

NOTE: in hardy you should install the older firmware and the wpa_supplicant package

For more info: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

