---
title: "Installation problem for ITE 9135 Generic DVB-T decoder"
date: 2012-08-01
forum: Multimedia Software
---

### Post by agomar on 2012-08-01
I am an absolute beginner.
I bough a dvb-t usb decoder and i am trying unsuccessfully to install on Ubuntu 12.04 LTS.
following the present situation:

fausto@fausto-desktop:~$ dmesg | grep dvb
[   30.539374] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[   30.697647] dvb-usb: downloading firmware from file 'dvb-usb-it9137-01.fw'
[18300.833581] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[18300.835835] dvb-usb: downloading firmware from file 'dvb-usb-it9137-01.fw'
fausto@fausto-desktop:~$

I went to
[https://help.ubuntu.com/community/DVB-T_%28USB%29](https://help.ubuntu.com/community/DVB-T_%28USB%29)
and I have performed the required installations.

I checked twice the firmware file, looks the right one. It is located on /lib/firmware

I don know how to proceed.....
thanks

---

### Post by daymz on 2012-09-18
Check out post #5 for a possible solution:
[http://ubuntuforums.org/showthread.php?t=1898046](http://ubuntuforums.org/showthread.php?t=1898046)

---

