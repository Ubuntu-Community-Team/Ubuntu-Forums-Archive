---
title: "Sierra Wireless 340U Ubuntu 12.04 AMD64 Server"
date: 2013-08-01
forum: Networking &amp; Wireless
---

### Post by miaviator278 on 2013-08-01
-------------------------
Manufacturer: Sierra Wireless, Incorporated
     Product: AirCard 340U
  Serial No.: XXX
-------------------------

uname -a
Linux XXX 3.5.0-36-generic #57~precise1-Ubuntu SMP Thu Jun 20 18:21:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise

lsusb
Bus 002 Device 007: ID 1199:9051 Sierra Wireless, Inc.

I have tried:
sudo modprobe usbserial vendor=0x1199 product=0x9051
[  191.236770] USB Serial deregistering driver Sierra USB modem
[  191.236809] usbcore: deregistering interface driver sierra
[  191.237679] USB Serial deregistering driver generic
[  191.237705] usbcore: deregistering interface driver usbserial_generic
[  191.237721] usbcore: deregistering interface driver usbserial
[  202.268461] usbcore: registered new interface driver usbserial
[  202.268482] usbcore: registered new interface driver usbserial_generic

No wwan or ttyUSB devices show up.

sudo apt-get install usb-modeswitch
usb_modeswitch -v 0x1199 -p 0x9051 -S 1 -W
Trying to send Sierra control message
USB error: error sending control message: Broken pipe
Error: sending Sierra control message failed (error -32). Aborting.

So far no way to start connectivity.

I also tried: 
[http://www.freedesktop.org/wiki/Software/ModemManager/SupportedDevices/](http://www.freedesktop.org/wiki/Software/ModemManager/SupportedDevices/)
sudo apt-get install modemmanager

which won't work since these are headless servers.

Any help would be appreciated.

---

### Post by ben24 on 2013-09-19
Have you had luck in this yet?  If so, how?

I'm running 13.04, but also have issues getting this device up and running.  If you have any updates, I'd appreciate it.

If you cd into /dev, ls, insert the USB modem, and ls again, diff the two and see if there's a new device.  I get cdc-wdm0
the usb_modeswitch doesn't work for me; I'm not so sure that's needed.

Here's my information:
```

$: uname -a
Linux XXX 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 19:56:49 UTC 2013 i686 i686 i686 GNU/Linux

$: lsusb
...
Bus 002 Device 004: ID 1199:9051 Sierra Wireless, Inc. 
...


```

Thanks for any ideas/info.

---

