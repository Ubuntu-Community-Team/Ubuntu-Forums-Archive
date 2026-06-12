---
title: "Ceton PCIe 6 - Can't read private key"
date: 2014-05-12
forum: Mythbuntu
---

### Post by jdmcmillian on 2014-05-12
Im trying to install Cetons 6 tuner PCIe card, 'make' goes fine with now errors,  But 'sudo make install' reports "Can't read private key" during the process. Which I believe is keeping the kernel from loading the driver.
After the install, and the 'sudo modprobe ctn91xx' command I can ping 192.168.200.2 (manually edited the interfaces file). 

```

media-center@media-center:~/install/ceton_infinitv_linux_driver$ sudo make install
Installing ctn91xx driver...
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-26-generic'
  INSTALL /home/media-center/install/ceton_infinitv_linux_driver/ctn91xx.ko
Can't read private key
  DEPMOD  3.13.0-26-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-26-generic'
cp 98-ctn91xx.rules /etc/udev/rules.d/
/sbin/depmod -a 3.13.0-26-generic
media-center@media-center:~/install/ceton_infinitv_linux_driver$

```

Is this normal, and if so why cant I access the card at 192.168.200.1? Any help would be appreciated. TIA

---

