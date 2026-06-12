---
title: "AT&amp;T USBComnnect Mercury issue"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by baker126 on 2010-04-19
Hi all...I recently installed the Beta of Lucid Kubuntu.  I switched from Gnome just to give KDE a try for awhile.  Coming from Karmic, my AT&T USBConnect worked "out of the box".  I initially switched to the Gnome version of Lucid and it worked there too.  After switching the KDE, it stopped.  The icon shows up in the tray, but I can't connect.

One thing I noticed that is different is when I set up a new connection, I don't get the drop drowns to select the carrier.  I attempted to Google for usernames, passwords and phone number from the connection, but none that I found work.

If I run tail -f /var/log/messages, the modem is detected as well as the microSD card installed.

"modinfo sierra" gives me this:

filename:       /lib/modules/2.6.32-21-generic/kernel/drivers/usb/serial/sierra.ko
license:        GPL
version:        v.1.3.8
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd, Elina Pasheva, Matthew Safar, Rory Filer
srcversion:     B0F0B63E667FF172A101231
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6893d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6892d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6891d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6890d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6880d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p685Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6859d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6856d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6855d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6853d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6852d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6851d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6850d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6839d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6838d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6835d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6834d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6833d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6832d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6816d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6815d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6813d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6812d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6809d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6808d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6805d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6804d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6803d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6802d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0029d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0026d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0025d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0023d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0112d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0224d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0220d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0218d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1E1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1B1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp0112d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           nmea:NMEA streaming (bool)
parm:           debug:Debug messages (bool)


I am sure this is just something I'm missing...probably something stupid...

Thanks.

---

### Post by alexfish on 2010-04-20
Hi

although not up on KDE

the commands for finding the modem id's should be the same

First boot up the computer without the device and post the results of

from the terminal 

Code:

tail -f /var/log/syslog

this will monitor what is happening in realtime, also hopping KDE uses same logging file

connect the modem and from a separate terminal

Code:

lsusb

this will show the device ID's, also will indicate if the device is been seen as storage or modem


Code:

dmesg | grep -e "modem" -e "tty" 

this will only give the output of the modem and any ports been used,also may show the version of driver for the modem

if a device or file shows up on the desk top then right click to safely remove or eject

issue the lsusb command again to see any changes in the ID's 

from the info of the outputs we could determine if the device is ready to be configured .IE if this device is actually as listed then it uses hso for connecting.  other software or a script  may be  required to get it recognised and working on the system . but can say for sure 

added can you compare the outputs with Ubuntu Gnome


regards

alexfish

---

