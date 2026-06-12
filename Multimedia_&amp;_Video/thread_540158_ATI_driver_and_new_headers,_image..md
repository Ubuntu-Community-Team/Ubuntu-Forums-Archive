---
title: "ATI driver and new headers, image."
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by mistermax on 2007-09-01
I followed the instructions -

sudo apt-get install fglrx-control

sudo dpkg -i xorg-driver-fglrx_8.39.4-1_i386.deb fglrx-kernel-source_8.39.4-1_i386.deb fglrx-amdcccle_8.39.4-1_i386.deb
sudo apt-get -f install
sudo rm /usr/src/fglrx-kernel-2.6.20-15-generic_8.36.5-1+2.6.20-15.27_i386.deb

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx

sudo module-assistant install fglrx

sudo mkdir /lib/modules/$(uname -r)/volatile

sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv


now, after that load of steps, I have nice 3D acceleration using th binary blob from ATI. However, I read that if I update my kernel this will all need to be re-run. Currently Update Manager is offering me
linux-headers-2.6.20-16, linux-headers-2.6.20-16-generic,linux-image-2.6.20-16,linux-libc-dev

My questioon is- will updating to these versions necessitate all the graphics config again?

---

### Post by jocko on 2007-09-02
I think you need to repeat these steps:
```
sudo rm /usr/src/fglrx*.deb

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx

sudo module-assistant install fglrx

sudo mkdir /lib/modules/$(uname -r)/volatile

sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
```

---

