---
title: "Lirc does not create a /dev"
date: 2008-03-07
forum: Mythbuntu
---

### Post by warnek2 on 2008-03-07
I have a unsupported IR chip set.  I am running Mythbuntu 7.10 and
the version of lirc (8.2) does not recognize my on-board IR receiver.

lsusb shows a device with ID= 1934:0602. I have done a lot of digging and  this device is a Fintek IR receiver. I went to the lirc snapshot web site and downloaded the latest (lirc-0.8.3pre1.tar.bz2). I looked in the lirc_mceusb2.c module and it shows the 1934 device ID as FINTEK.
I compiled the code and the module loaded OK, but there are still two big problems. 1) Still no device is created (I did it manually with mknod but that doesn't help) 2) I'm getting "tainted kernel" messages in syslog.

Any ideas when mythbuntu will get a later version of lirc built-in and is there something else I can look at to debug this issue?

I followed all of the instructions in the ubuntu lirc istall pages. Like I said, it compiles with no errors, it just doesn't work. Anyone else using an aopen MP965-DR platform?

Thanks in advance.
Keith

---

### Post by fdemmer on 2008-03-16
i installed lirc from cvs yesterday (2008-03-15) *over* a previous installation via apt-get:

dmesg:
```
[   34.704532] lirc_dev: IR Remote Control driver registered, at major 61
[   34.722814] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   34.722818] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   34.730514] usbcore: registered new interface driver lirc_mceusb2
```

the node created is /dev/lircd
```
root@blackpearl:~# ls -la /dev|grep lirc
srw-rw-rw-  1 root   root           0 2008-03-16 12:11 lircd
```

when running irw, the daemon crashes:
```
root@blackpearl:/var/log# lircd -n
lircd: lircd(mceusb2) ready
lircd: accepted new client on /dev/lircd
lircd: could not get file information for /dev/lirc
lircd: default_init(): No such file or directory
lircd: caught signal
Terminated
```

makes sense, because ther is no /dev/lirc. but why is there none?

the "make install" installed the *.ko in the misc directory, while the lirc *.deb package in ubuntu/media/lirc

```
root@blackpearl:/lib/modules# find /lib/modules -name lirc_mceusb2.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_mceusb2/lirc_mceusb2.ko
/lib/modules/2.6.22-14-generic/misc/lirc_mceusb2.ko
root@blackpearl:/lib/modules# ls -la /lib/modules/2.6.22-14-generic/misc/lirc_mceusb2.ko
-rw-r--r-- 1 root root 151492 2008-03-15 19:21 /lib/modules/2.6.22-14-generic/misc/lirc_mceusb2.ko
root@blackpearl:/lib/modules# ls -la /lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_mceusb2/lirc_mceusb2.ko
-rw-r--r-- 1 root root 19688 2007-10-13 07:43 /lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_mceusb2/lirc_mceusb2.ko
```

so i moved the cvs-modules to the "ubuntu-way" directories, over writing the old ones:
```
root@blackpearl:/# mv /lib/modules/2.6.22-14-generic/misc/lirc_dev.ko /lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_dev
root@blackpearl:/# mv /lib/modules/2.6.22-14-generic/misc/lirc_mceusb2.ko /lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_mceusb2
```

removed already loaded modules and restarted lircd:
```
root@blackpearl:/# rmmod lirc_mceusb2
root@blackpearl:/# rmmod lirc_dev
root@blackpearl:/# lsmod|grep lirc
root@blackpearl:/# /etc/init.d/lirc restart
```

now the missing node is here:
```
root@blackpearl:/var/log# ls -la /dev|grep lirc
crw-rw----  1 root   root     61,   0 2008-03-16 12:39 lirc0
srw-rw-rw-  1 root   root           0 2008-03-16 12:39 lircd
```

and there is also more information in dmesg:
```
[ 1734.902035] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[ 1735.052172] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 1735.056005] lirc_mceusb2[2]: FINTEK eHome Infrared Transceiver on usb4:2
```

also irw is working:
```
root@blackpearl:/# irw
000000037ff07bdd 00 OK mceusb
000000037ff07bdd 01 OK mceusb
000000037ff07bdd 00 OK mceusb
```

---

### Post by milan960 on 2009-04-15
I'm struggling to get remote working with my Aopen MP965-DR system. I installed a MC770A TV tuner card in it. I installed Debian lenny amd64.

Remote wouldn't work from debian packages so I downloaded and built lirc from the lirc.org site. When I run "mode2", things do appear on the screen, so I guess, hardware is there and working. However, when I run "irw" I don't get anything out. I configured lirc to use mceusb configuration file, which I found in many places.

THE CONFUSING BIT:
==================

When I checked dmesg output, it seems as if I actually have 2 (TWO!) IR transceivers: the first one reported is:

lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.80$

. The second one appears like:

lirc_mceusb2[2]: FINTEK eHome Infrared Transceiver on usb3:2

I suspect this may be due to the TV tuner card, although the card itself is fully enclosed in the unit and has no visible parts that one may think are IR sensors.

I suspect maybe lircd daemon I got with debian distro may not be up-to-date, but then it was released only a few months ago.

Anyway, to put things simply: has anyone managed to get remote working on mp965 and what was hardware/software configuration?

Many thanks
Milan

---

