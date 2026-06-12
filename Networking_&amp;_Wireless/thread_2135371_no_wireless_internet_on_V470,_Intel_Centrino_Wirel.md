---
title: "no wireless internet on V470, Intel Centrino Wireless-N 1000"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by ikki_72 on 2013-04-14
$ lspci | grep -i network
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

$ lsb_release -r
Release:	12.04

$ uname -a
Linux Lenovo-V470 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

i managed to connect to my wireless network but not able to browse to internet

basically what I had tried:

1- download iwlwifi-1000-ucode-128.50.3.1.tgz
2- copy and rename iwlwifi-1000-3.ucode as iwlwifi-1000-5.ucode into /lib/firmware/
3- restart my laptop

but still the same. Internet access with Ethernet is working.

---

### Post by ikki_72 on 2013-04-14
solution found:

make sure in /etc/modprobe.d/iwlwifi.conf
**options iwlwifi 11n_disable=1**

reboot

---

### Post by RichardET on 2013-08-17
So 13.04 will not work on a V470 without tweaking?

---

### Post by ikki_72 on 2013-08-25
yes it will but beware of uefi partition

you might have to create a small 50mb uefi partition and use boot-repair after installation from live installation media

---

