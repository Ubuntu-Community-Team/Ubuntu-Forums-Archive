---
title: "multiple DVB-T usb tuner failure"
date: 2013-10-18
forum: Multimedia Software
---

### Post by lage-sjoblom on 2013-10-18
Hi all.
I hope this is the right place for this post. If not, let me know.
I have 2 DVB-T usb sticks that i can´t get to coexist.
One is an noname based on the Afatech AF9015 chip, the other one is a PCTV nanoStick T2 290e based on Sony CXD2820R.
Running ubuntu server 13.10 and TVHeadend3.4.27 on a VIA Artigo.
On the same server i also run OWFS and som 1-wire temp sensors via a Dallas Semiconductor DS1490F 2-in-1 Fob, 1-Wire adapter.
Whe i run them one at a time it works fine, but when both are plugged in, i get syslog filled with this after a while:
```
Oct 18 00:15:10 Skeppsmaln209 kernel: [  258.234774] i2c i2c-2: cxd2820r: i2c rd failed=-5 reg=10 len=1
Oct 18 00:15:10 Skeppsmaln209 kernel: [  258.288885] em28174 #0: writing to i2c device at 0xd8 failed (error=-5)
Oct 18 00:15:10 Skeppsmaln209 kernel: [  258.288910] i2c i2c-2: cxd2820r: i2c rd failed=-5 reg=10 len=1
Oct 18 00:15:10 Skeppsmaln209 kernel: [  258.343027] em28174 #0: writing to i2c device at 0xd8 failed (error=-5)
Oct 18 00:15:10 Skeppsmaln209 kernel: [  258.343052] i2c i2c-2: cxd2820r: i2c rd failed=-5 reg=10 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.397169] em28174 #0: writing to i2c device at 0xd8 failed (error=-5)
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.397195] i2c i2c-2: cxd2820r: i2c rd failed=-5 reg=10 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.451304] em28174 #0: writing to i2c device at 0xd8 failed (error=-5)
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.451329] i2c i2c-2: cxd2820r: i2c rd failed=-5 reg=10 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.484068] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.484089] i2c i2c-3: af9013: i2c rd failed=-71 reg=d507 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.488392] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.488424] i2c i2c-3: af9013: i2c rd failed=-71 reg=d330 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.492634] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.492659] i2c i2c-3: af9013: i2c rd failed=-71 reg=d417 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.496979] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.497004] i2c i2c-3: af9013: i2c wr failed=-71 reg=d417 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.501089] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.505340] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.505364] i2c i2c-3: af9013: i2c rd failed=-71 reg=d417 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.505447] em28174 #0: writing to i2c device at 0xd8 failed (error=-5)
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.505466] i2c i2c-2: cxd2820r: i2c rd failed=-5 reg=10 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.509594] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.509619] i2c i2c-3: af9013: i2c wr failed=-71 reg=d417 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.509636] __tda18271_write_regs: [3-00c0|M] ERROR: idx = 0x5, len = 1, i2c_transfer returned: -71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.509650] tda18271_init: [3-00c0|M] error -71 on line 832
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.509663] tda18271_tune: [3-00c0|M] error -71 on line 910
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.509683] tda18271_set_params: [3-00c0|M] error -71 on line 985
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.513911] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.513946] i2c i2c-3: af9013: i2c rd failed=-71 reg=d330 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.518097] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.518122] i2c i2c-3: af9013: i2c wr failed=-71 reg=d330 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.522344] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.522369] i2c i2c-3: af9013: i2c rd failed=-71 reg=d507 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.526593] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.526617] i2c i2c-3: af9013: i2c wr failed=-71 reg=d507 len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.530849] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.530873] i2c i2c-3: af9013: i2c rd failed=-71 reg=9bfe len=1
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.535100] usb 1-2: dvb_usb_v2: usb_bulk_msg() failed=-71
Oct 18 00:15:11 Skeppsmaln209 kernel: [  258.535124] i2c i2c-3: af9013: i2c wr failed=-71 reg=9bfe len=1

```
When i stop TVheadend, the log flooding ends.
I have the latest fw for the AF9015.
After reading some other thread i also tried adding this to /etc/modprobe.d/dvb-options.conf
```
options dvb_usb_v2 disable_rc_polling=1
options rc_core disable_rc_polling=1

```
but with no result.

If anyone can point me in the right direction to solve this, I´d be very greatful.

Regards,
Lage

---

### Post by M7CPn4b on 2013-10-18
Are they on the same USB controller? And if yes, have you tried to connect them to different ones? (If possible)

-Emily

---

### Post by lage-sjoblom on 2013-10-18
> **M7CPn4b said:**
> Are they on the same USB controller? And if yes, have you tried to connect them to different ones? (If possible)

-Emily

There are 4 usb ports available, but moving them around doesn´t seem to change much. Maybe they share the same controller? Not sure how to tell...
This is how it looks after a reboot:
```

root@Skeppsmaln209:~# dmesg|grep usb
[    0.218968] usbcore: registered new interface driver usbfs
[    0.219009] usbcore: registered new interface driver hub
[    0.219094] usbcore: registered new device driver usb
[    2.514206] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.514217] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.514227] usb usb1: Product: EHCI Host Controller
[    2.514237] usb usb1: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    2.514247] usb usb1: SerialNumber: 0000:00:10.4
[    2.515830] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    2.515841] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.515851] usb usb2: Product: UHCI Host Controller
[    2.515861] usb usb2: Manufacturer: Linux 3.11.0-12-generic uhci_hcd
[    2.515871] usb usb2: SerialNumber: 0000:00:10.0
[    2.517163] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    2.517173] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.517184] usb usb3: Product: UHCI Host Controller
[    2.517194] usb usb3: Manufacturer: Linux 3.11.0-12-generic uhci_hcd
[    2.517203] usb usb3: SerialNumber: 0000:00:10.1
[    2.562017] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.562027] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.562037] usb usb4: Product: UHCI Host Controller
[    2.562047] usb usb4: Manufacturer: Linux 3.11.0-12-generic uhci_hcd
[    2.562057] usb usb4: SerialNumber: 0000:00:10.2
[    2.900114] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    3.037904] usb 1-1: New USB device found, idVendor=15a4, idProduct=9016
[    3.037920] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.037931] usb 1-1: Product: USB2.0 DVB-T TV Stick
[    3.037941] usb 1-1: Manufacturer: NEWMI
[    3.037951] usb 1-1: SerialNumber: 010103120800001
[    3.408101] usb 1-3: new high-speed USB device number 4 using ehci-pci
[    3.541066] usb 1-3: New USB device found, idVendor=2013, idProduct=024f
[    3.541081] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.541092] usb 1-3: Product: PCTV 290e
[    3.541102] usb 1-3: Manufacturer: PCTV Systems
[    3.541111] usb 1-3: SerialNumber: 00000006LG3Z
[    3.686614] usbcore: registered new interface driver usbhid
[    3.686625] usbhid: USB HID core driver
[    3.725203] input: NEWMI USB2.0 DVB-T TV Stick as /devices/pci0000:00/0000:00:10.4/usb1/1-1/1-1:1.1/input/input3
[    3.727333] hid-generic 0003:15A4:9016.0001: input,hidraw0: USB HID v1.01 Keyboard [NEWMI USB2.0 DVB-T TV Stick] on usb-0000:00:10.4-1/input1
[    3.796075] usb 2-2: new full-speed USB device number 2 using uhci_hcd
[    3.958862] usb 2-2: New USB device found, idVendor=04fa, idProduct=2490
[    3.958878] usb 2-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   29.077786] usb 1-1: dvb_usb_v2: found a 'Afatech AF9015 reference design' in warm state
[   29.100836] usbcore: registered new interface driver em28xx
[   29.513847] usb 1-3: DVB: registering adapter 1 frontend 0 (Sony CXD2820R)...
[   29.644510] input: em28xx IR (em28174 #0) as /devices/pci0000:00/0000:00:10.4/usb1/1-3/rc/rc0/input8
[   29.646638] rc0: em28xx IR (em28174 #0) as /devices/pci0000:00/0000:00:10.4/usb1/1-3/rc/rc0
[   29.668845] usb 1-1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[   29.778064] usb 1-1: DVB: registering adapter 2 frontend 0 (Afatech AF9013)...
[   30.060122] input: Afatech AF9015 reference design as /devices/pci0000:00/0000:00:10.4/usb1/1-1/rc/rc1/input9
[   30.060658] rc1: Afatech AF9015 reference design as /devices/pci0000:00/0000:00:10.4/usb1/1-1/rc/rc1
[   30.060680] usb 1-1: dvb_usb_v2: schedule remote query interval to 500 msecs
[   30.060695] usb 1-1: dvb_usb_v2: 'Afatech AF9015 reference design' successfully initialized and connected
[   30.073995] usbcore: registered new interface driver dvb_usb_af9015
root@Skeppsmaln209:~# lsusb
Bus 001 Device 004: ID 2013:024f PCTV Systems nanoStick T2 290e
Bus 001 Device 002: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04fa:2490 Dallas Semiconductor DS1490F 2-in-1 Fob, 1-Wire adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
/Lage

---

### Post by M7CPn4b on 2013-10-18
Hmm, not sure what's going on, as everything works independently, I doubt that it is software problem. I know that DVB-S cards and sticks suck a lot of electricity. Could it be that that two of them pull too much? Do you have the opportunity to use a USB hub with a separate power supply? I would try to connect them to a hub, or at least one of them.

Do the sticks work individually on any of the USB ports? 

-Emily

---

### Post by lage-sjoblom on 2013-10-18
Yes, as i mentioned in the first post running them one at a time works fine, so maybe it´s a power issue. Don´t have a hub so i can´t test now but I´ll get one.

---

### Post by M7CPn4b on 2013-10-18
> **lage-sjoblom said:**
> Yes, as i mentioned in the first post running them one at a time works fine, so maybe it´s a power issue. Don´t have a hub so i can´t test now but I´ll get one.

What I meant was, does every stick work in every USB port? (there are ports with high and low current)

-Emily

---

### Post by lage-sjoblom on 2013-10-18
Yes, they do.

---

### Post by mprice2010 on 2014-05-15
Hi

I am having the exact issue? Was there ever a solution to this???

Thanks

---

