---
title: "DVB-S PCTV 400e firmware not found"
date: 2013-03-16
forum: Multimedia Software
---

### Post by xtrailrunner on 2013-03-16
Hello,
I tried to setup Pinnacle device DVB-S PCTV 400e with my Ubuntu 11.04.

The device is detected:
lsusb
=> Bus 001 Device 004: ID 2304:020f Pinnacle Systems, Inc. PCTV 400e BDA Device

I have copied firmware file "dvb-usb-pctv-400e-01.fw" to /lib/firmware and rebooted.

But it seems that the firmware is not found (owner is root and permissions are fine).
dmesg | grep dvb
[   30.564723] dvb-usb: found a 'Pinnacle 400e DVB-S USB2.0' in cold state, will try to load a firmware
[   30.569236] dvb-usb: did not find the firmware file. (dvb-usb-pctv-400e-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[   30.569281] usbcore: registered new interface driver dvb_usb_ttusb2

After a short while I get a message from the system that I should reboot to complete updates.

Can someone help with advice. I really don't know what happens here.

---

### Post by xtrailrunner on 2013-03-16
Solved.
I had to remove the USB and plugin again. Than it worked.

---

