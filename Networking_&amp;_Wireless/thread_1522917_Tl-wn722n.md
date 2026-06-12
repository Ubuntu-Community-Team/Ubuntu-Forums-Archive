---
title: "Tl-wn722n"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by c0rrupt.own on 2010-07-02
Hello
I have ubuntu 10.04 32bit and I try install driver for TL-WN722N from [http://www.linuxwireless.org](http://www.linuxwireless.org) and I try ndiswrapper and compatibile backports from repozitory. All three methods dont work. Any one know how to do it? Can you please help me and tell me how exactly install it? I googling, reading forums, installing, compiling, reinstalling 3 days and still nothing. Im stupid or I do somthing wrong.
Thank you very much for any help.

---

### Post by c0rrupt.own on 2010-07-03
Some one on another forum tell me to try it again from linuxers. I download last compatibile...tar make, make install, copy ar9271.fw to /lib/firmware and restart. No errors in installation, no error on startup I think, but wifi still not working.

here is whole dmesg [http://c0rrupt.cz/dmesg.txt](http://c0rrupt.cz/dmesg.txt)
```

dmesg | grep usb
[ 0.406670] usbcore: registered new interface driver usbfs
[ 0.406715] usbcore: registered new interface driver hub
[ 0.406802] usbcore: registered new device driver usb
[ 0.736291] usb usb1: configuration #1 chosen from 1 choice
[ 0.737103] usb usb2: configuration #1 chosen from 1 choice
[ 0.737739] usb usb3: configuration #1 chosen from 1 choice
[ 0.738379] usb usb4: configuration #1 chosen from 1 choice
[ 0.739045] usb usb5: configuration #1 chosen from 1 choice
[ 1.084103] usb 1-1: new high speed USB device using ehci_hcd and address 2
[ 1.241840] usb 1-1: configuration #1 chosen from 1 choice
[ 1.352096] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 1.518991] usb 1-2: configuration #1 chosen from 1 choice
[ 1.880091] usb 3-2: new low speed USB device using uhci_hcd and address 2
[ 2.048947] usb 3-2: configuration #1 chosen from 1 choice
[ 2.081595] usbcore: registered new interface driver hiddev
[ 2.100597] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input6
[ 2.100935] generic-usb 0003:15CA:00C3.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2/input0
[ 2.101019] usbcore: registered new interface driver usbhid
[ 2.101030] usbhid: v2.6:USB HID core driver
[ 15.453342] usbcore: registered new interface driver ndiswrapper
[ 15.674597] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input8
[ 15.674786] usbcore: registered new interface driver uvcvideo

dmesg | grep ath9
[ 16.814315] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 16.814342] ath9k 0000:01:00.0: setting latency timer to 64
[ 17.032310] phy0: Selected rate control algorithm ‘ath9k_rate_control’
[ 17.034676] Registered led device: ath9k-phy0::radio
[ 17.034746] Registered led device: ath9k-phy0::assoc
[ 17.034815] Registered led device: ath9k-phy0::tx
[ 17.034882] Registered led device: ath9k-phy0::rx

```
```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b175 Chicony Electronics Co., Ltd
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Any help how to repair it? Im quite a noob.

---

### Post by vagrale13 on 2010-07-05
The  continuity from here [http://ubuntuforums.org/showthread.php?p=9547822#post9547822](http://ubuntuforums.org/showthread.php?p=9547822#post9547822)

Why you install *ndiswrapper*?? :???:
I think this is the problem where doesn' t work!
[B]
ath9k_htc[/B] support your chipset [http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices](http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices)
i don' t test it, but i think must be works! :)

I think  now, after install *ndiswrapper,* is a little difficult to   make it work! :-k
The *ndiswrapper* is the  last option where we must try to do!

---

