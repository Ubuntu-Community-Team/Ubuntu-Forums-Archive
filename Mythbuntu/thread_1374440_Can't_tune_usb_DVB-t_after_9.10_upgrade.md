---
title: "Can't tune usb DVB-t after 9.10 upgrade"
date: 2010-01-06
forum: Mythbuntu
---

### Post by AlecJ on 2010-01-06
I have upgraded online from 9.04 to 9.10.

I have lost my TwinhanDTV USB-Ter during the upgrade.

It is unable to lock or receive any channels anymore.

Here is the results of 'dmesg |grep dvb'
```
alectv@alectv-desktop:~$ dmesg |grep dvb
[    6.934625] saa7146: register extension 'budget_ci dvb'.
[    6.952294] dvb-usb: found a 'TwinhanDTV USB-Ter USB1.1 / Magic Box I / HAMA USB1.1 DVB-T device' in cold state, will try to load a firmware
[    6.952299] usb 5-2: firmware: requesting dvb-usb-dibusb-5.0.0.11.fw
[    6.962747] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[    6.962750] usb 3-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[    7.040288] budget_ci dvb 0000:01:08.0: PCI INT A -> Link[LNKC] -> GSI 17 (level, low) -> IRQ 17
[    7.101261] input: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:08.0/0000:01:08.0/input/input3
[    7.443894] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[    7.488715] dvb-usb: downloading firmware from file 'dvb-usb-dibusb-5.0.0.11.fw'
[    7.924247] budget_ci dvb 0000:01:09.0: PCI INT A -> Link[LNKD] -> GSI 19 (level, low) -> IRQ 19
[    7.991671] input: Budget-CI dvb ir receiver saa7146 (1) as /devices/pci0000:00/0000:00:08.0/0000:01:09.0/input/input5
[    8.035892] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[    8.035895] cx88/2: registering cx8802 driver, type: dvb access: shared
[    8.181277] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[    8.181337] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.998081] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    9.003048] usbcore: registered new interface driver dvb_usb_dibusb_mb
[    9.004920] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[    9.601558] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[    9.601715] usbcore: registered new interface driver dvb_usb_dib0700
[   11.391482] dvb-usb: found a 'TwinhanDTV USB-Ter USB1.1 / Magic Box I / HAMA USB1.1 DVB-T device' in warm state.
[   11.411327] dvb-usb: will use the device's hardware PID filter (table count: 16).
[   11.881265] dvb-usb: TwinhanDTV USB-Ter USB1.1 / Magic Box I / HAMA USB1.1 DVB-T device successfully initialized and connected.
```

As you can see it loads ok.
Worked fine on 9.04.
I'm useing the daily builds version of 9.10, in the hope there is a fix.

---

