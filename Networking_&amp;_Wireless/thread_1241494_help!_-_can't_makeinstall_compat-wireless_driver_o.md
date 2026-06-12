---
title: "help! - can't make/install compat-wireless driver on thinkpad r400"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by chiangs on 2009-08-16
after installing ubuntu 9.04 on my thinkpad, i can't detect wireless connections and can only go online via ethernet. 

i've tried to install a wireless driver but seem to have run into these ugly problems...

administrator@administrator-laptop:/usr/src/compat-wireless-2008-10-31$ sudo make install

and this is what i get...
make -C /lib/modules/2.6.28-14-generic/build M=/usr/src/compat-wireless-2008-10-31 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
scripts/Makefile.build:41: /usr/src/compat-wireless-2008-10-31/drivers/net/wireless/libertas_tf/Makefile: No such file or directory
make[4]: *** No rule to make target `/usr/src/compat-wireless-2008-10-31/drivers/net/wireless/libertas_tf/Makefile'.  Stop.
make[3]: *** [/usr/src/compat-wireless-2008-10-31/drivers/net/wireless/libertas_tf] Error 2
make[2]: *** [/usr/src/compat-wireless-2008-10-31/drivers/net/wireless] Error 2
make[1]: *** [_module_/usr/src/compat-wireless-2008-10-31] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [modules] Error 2
administrator@administrator-laptop:/usr/src/compat-wireless-2008-10-31$ 

what is error 2? i've tried ./configure but it comes up as no such file or directory detected. 

can someone help? i really dont want to be stuck using ethernet when my new laptop has wireless -_- thanks!!

---

### Post by stlsaint on 2009-08-16
i had the same issue...actually i still have the no wireless issue but try this for the make install..split them into two seperate cmds...it worked to install the drivers for me but still no internet!!

when your in the directory you want to be in with your driver files do this:

sudo make
(after its done do...)
sudo install

---

### Post by chiangs on 2009-08-16
> **stlsaint said:**
> it worked to install the drivers for me but still no internet!!


so what do you use?

---

### Post by AmerNewbieInDE on 2009-08-16
cd to the directory

sudo make compat-wireless-2008-10-31

then when it is done

sudo make install compat-wireless-2008-10-31

---

