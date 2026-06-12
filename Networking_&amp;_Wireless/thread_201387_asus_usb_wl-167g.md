---
title: "asus usb wl-167g"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by superbob666 on 2006-06-21
hi guys;


i m trying to install asus wireless usb, wl-167g:

make[1]: Entering directory `/lib/modules/2.6.12-9-386'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386'
make: *** [all] Error 2

but i get the abover errors, i m using the drivers provided at asus site. any help will be most appreciated

thankx

---

### Post by noname101 on 2006-06-21
You probably need the kernel source.
```
sudo apt-get install linux-source-2.6.12
cd /usr/src
sudo tar xvjf linux-source-2.6.12.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
sudo ln -s /usr/src/linux /lib/modules/2.6.12-10-k7/build
cd linux
sudo make oldconfig
sudo make include/linux/version.h
sudo make modules
```

---

### Post by Tobbz on 2006-06-22
I would recommend the rt2570 driver from Serialmonkey.com
I am using that same Asus USB stick.

Get the latest rt2570 USB nightly CVS tarball here:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

I haven't got it work stabile with WPA encryption, but it's stabile using WEP.

---

