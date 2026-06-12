---
title: "Pinnacle hdtv 320e stick problems"
date: 2010-02-11
forum: Multimedia Software
---

### Post by bagbiter on 2010-02-11
first version: 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

so i am following these instructions to install a hdtv usb stick that supposedly is using the em28xx-drivers.

> sudo su

apt-get install mercurial linux-headers-$(uname -r) linux-source build-essential

cd /lib/firmware

wget [http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz](http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz)

tar xvzf firmware_v4.tgz

hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)

cd v4l-dvb-experimental

make

make install

reboot

sudo modprobe em2880-dvb

If on the next reboot, the card stops working the em2880-dvb module is not being loaded properly in Feisty. To fix this :

cd /etc/modprobe.d
sudo gedit dvbstick

then add this line to the new dvbstick file :
install em28xx /sbin/modprobe --ignore-install em28xx; /bin/sleep 2; /sbin/modprobe em2880-dvb

reboot and it should be back up and running.

i have tried what it says, but i get this error when running modprobe em2880-dvb:
> WARNING: All config files need .conf: /etc/modprobe.d/dvbstick, it will be ignored in a future release.
FATAL: Module em2880_dvb not found.

i have also tried modprobe em28xx:
> WARNING: All config files need .conf: /etc/modprobe.d/dvbstick, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/dvbstick, it will be ignored in a future release.
FATAL: Error inserting em28xx (/lib/modules/2.6.31-19-generic/kernel/drivers/media/video/em28xx/em28xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: All config files need .conf: /etc/modprobe.d/dvbstick, it will be ignored in a future release.
FATAL: Module em2880_dvb not found.
FATAL: Error running install command for em28xx


PS i had to hg clone the files from other sites because the one in instructions is down

---

### Post by bagbiter on 2010-02-12
too soon to bump?

---

### Post by bagbiter on 2010-02-12
Ok never mind this, then. I will just buy a new one.

Does anyone know of a good USB h264 dvb-t that is easy to set up in ubuntu?

---

