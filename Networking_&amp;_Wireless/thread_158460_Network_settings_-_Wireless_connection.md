---
title: "Network settings - Wireless connection?"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by monomaniacpat on 2006-04-11
Hi guys,

I'm trying various methods for installing a driver for my DWLG122 wireless USB dongle, and I've followed the instructions [here](https://wiki.ubuntu.com/NdisWrapper_DWL-G122?highlight=%28g122%29%7C%28dwl%29), but I can't select the 'Wireless connnection' because there isn't one under Network settings.

What do I do?

---

### Post by Darkriser on 2006-04-11
if your usb wifi adapter uses ralink chpset, isn't it easier to set it up following way?
[http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers)

this worked for me absolutely great.
yes, and don't forget to run this code (see below) prior to compiling.

sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4

---

### Post by monomaniacpat on 2006-04-11
Yes, I've already tried that, but I'm waiting on a reply from someone regarding the process. In the meantime I thought I'd try ndiswrapper - does anyone know what I need to do?

---

### Post by Darkriser on 2006-04-11
aaah, ok.
anyway, ndiswrapper uses proprietary (closed) drivers and the installation can be a pain while rt2x00 is an opensource project (driver) and the set-up is pretty easy and straight-forward.

---

### Post by monomaniacpat on 2006-04-11
Well maybe you could tell me what to do in the following situation from [here](http://www.ubuntuforums.org/showthread.php?t=106846&page=6)

[QUOTE=monomaniacpat]I managed to find out my SSID and gedit'd the file accordingly... Having followed the next couple of commands, I produce this response:

```
patrick@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ ok ]
patrick@ubuntu:~$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device

```

What am I doing wrong?[/QUOTE]

Thanks.

---

### Post by Darkriser on 2006-04-11
there are two VERY important steps in rt2x00 installation (applicable especially for Ubuntu).

first) sudo mv /etc/modprobe.conf /etc/modutils/rt2570
second) sudo mv /lib/modules/2.6.xx/extra/rt2570.ko /lib/modules/2.6.xx-xx-xxx/kernel/drivers/net/wireless/rt2570.ko

(exactly like stated here: [http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers))

only after that you can install the module:
sudo depmod -a
sudo update-modules
sudo modprobe rt2570

and try bringing it up:
sudo ifup rausb0

---

### Post by monomaniacpat on 2006-04-11
Unfortunately, I've already done that.... :(

---

### Post by Darkriser on 2006-04-11
and can you confirm that:
* /etc/modutils/rt2570 exists (pls, post here output of 'cat /etc/modutils/rt2570' command)
* /lib/modules/2.6.xx-xx-xxx/kernel/drivers/net/wireless/rt2570.ko exists (try ls -la /lib/modules/2.6.xx-xx-xxx/kernel/drivers/net/wireless/rt2570.ko) ?

moreover, post pls output of 'sudo lsmod' command.

---

