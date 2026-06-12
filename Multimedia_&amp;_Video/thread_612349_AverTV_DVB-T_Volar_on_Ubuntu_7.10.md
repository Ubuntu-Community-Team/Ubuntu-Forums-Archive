---
title: "AverTV DVB-T Volar on Ubuntu 7.10"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by Castellan on 2007-11-13
I see some other people have had the same problem as me trying to get an AverMedia AverTV DVB-T Volar to work on Ubuntu.

I have used [http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto](http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto) and the information at linuxtv.org to get as far as this...

I have checked that the right firmware is in the right place and /lib/firmware/2.6.22-14-generic has dvb-usb-avertv-a800-02.fw However, I noticed in syslog that when I plug in the device I get 

Nov 14 01:10:10 charles-desktop kernel: [ 9440.226907] usb 2-3.4: new high speed USB device using ehci_hcd and address 8
Nov 14 01:10:10 charles-desktop kernel: [ 9440.319725] usb 2-3.4: configuration #1 chosen from 1 choice
Nov 14 01:10:10 charles-desktop kernel: [ 9440.319938] dvb-usb: found a 'AVerMedia AVerTV DVB-T Volar' in cold state, will try to load a firmware
Nov 14 01:10:10 charles-desktop NetworkManager: <debug> [1195002610.118978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_7ca_b808_300089700333'). 
Nov 14 01:10:10 charles-desktop firmware_helper[8884]: main: error loading '/lib/firmware/dvb-usb-dib0700-01.fw' for device '/class/firmware/2-3.4' with driver 'usb'
Nov 14 01:10:10 charles-desktop kernel: [ 9440.333640] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
Nov 14 01:10:10 charles-desktop NetworkManager: <debug> [1195002610.148836] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_7ca_b808_300089700333_if0'). 
Nov 14 01:10:10 charles-desktop NetworkManager: <debug> [1195002610.171337] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_7ca_b808_300089700333_usbraw'). 

So it looks as though it is loading the wrong firmware, from goodness knows where? Or am I reading this all wrong?

If I'm not is there some way that I can get Ubuntu to look in the 'right' place and look for the right firmware? I am in way over my head with this, but any help is really appreciated.

---

### Post by Hugolp on 2008-02-17
I think this page will solve your problem if you still have it: [http://www.mythtv.org/wiki/index.php/AVerTV_DVB-T_Volar](http://www.mythtv.org/wiki/index.php/AVerTV_DVB-T_Volar)

Just watch out and copy it under the right kernel directory in my case the second order was like this:

"sudo cp dvb-usb-dib0700-03-pre1.fw /lib/firmware/2.6.22-14-generic/dvb-usb-dib0700-01.fw"

To check your kernel version just go to the /lib/firmware directory and check wich directories you have (if you have more than one, you are probably using the modern one, the one with higher numbers).

Hugo

---

