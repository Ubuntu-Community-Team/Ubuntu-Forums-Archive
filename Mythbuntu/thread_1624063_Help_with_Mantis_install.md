---
title: "Help with Mantis install"
date: 2010-11-17
forum: Mythbuntu
---

### Post by eriksson25 on 2010-11-17
Hi, I have a cinergy c HD, I had it runing on 10.10 just fine, with the s2-liplianin Mantis drivers following this guide
[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C](http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C)

But got a hdd crash so had to reinstall, and then I thought I was gone try the dkms version. But that locked up the computer and it woulden boot corectly until I removed the tv card. So uninstalled that dkms driver and now it boot with tv card in but once Again I have no Mantis driver. So I thought I was gone try as last time. But keep getting a strange error that I cant solve.

```
eriksson25@eriksson25:~/s2-liplianin$ make
make -C /home/eriksson25/s2-liplianin/v4l
make[1]: Entering directory `/home/eriksson25/s2-liplianin/v4l'
No version yet, using 2.6.36-020636rc7-generic
make[1]: Leaving directory `/home/eriksson25/s2-liplianin/v4l'
make[1]: Entering directory `/home/eriksson25/s2-liplianin/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.36
File not found: /lib/modules/2.6.36-020636rc7-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: Leaving directory `/home/eriksson25/s2-liplianin/v4l'
make[1]: Entering directory `/home/eriksson25/s2-liplianin/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.36
File not found: /lib/modules/2.6.36-020636rc7-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/eriksson25/s2-liplianin/v4l'
make: *** [all] Error 2

```

As you can se I have even tried to install new kernel to get it to work, it was the same error with the old 2.6.35 kernel.

Please, is there someone that can help me out.

---

### Post by LowSky on 2010-11-17
It says right on that link provided you dont need to install any drivers since kernel 2.6.33

---

### Post by eriksson25 on 2010-11-17
> **LowSky said:**
> It says right on that link provided you dont need to install any drivers since kernel 2.6.33

Yes, but if one investigates further it is crappy driver that dont work that is included. It might work to 2-6-37 but not sure yet.

Well, found the solution

sudo modprobe tda10021
sudo modprobe mantis

If anyone els it finding this.

---

