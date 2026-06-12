---
title: "howto install TP Link TL WN422G on Lucid"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by barong234 on 2012-02-03
It's work on my Ubuntu 10.04 with kernel 2.x.
Okai, first thing first

[LIST]
[*]Download [firmware]("http://ubuntuforums.org/from%20http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=ar9271.fw;h=2398e5517b0ad7da7adad54763b91705a3d2acb7;hb=HEAD")  and add to /lib/firmware
[*]Download the [driver]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2")
[/LIST]
After done adding the firmware and download the driver, run

$ tar xjvf compat-wireless-2.6.tar.bz2 
$ cd compat-wireless-2.6. 
$ ./scripts/driver-select ath9k_htc 
$ make && sudo make install

[FONT=Verdana]reboot the computer, plug the usb wireless and enjoy... :D[/FONT]

---

### Post by Marcelo01 on 2012-04-01
Hi barong1234,

I've tried your instructions but I can't get my TL-Wn422G v2 work on my Ubuntu 11.10 that is running virtualized in Virtualbox.

I'm able to see the USB connected through "lsusb" command, but after all procedures still not able to use it. It does not show in "iwconfig" , "ifconfig".

Is there any alternative solution or test that I can made?
Are there any difficulties to use this wireless adapter in virtualized O.S ?

Thanks!

---

### Post by Marcelo01 on 2012-04-05
Have found the problem, is related to VirtualBox.. it can handle very well with USB passtrhough to guest OS.
Just run in VmWare and it runs fine, just OOTB.

---

