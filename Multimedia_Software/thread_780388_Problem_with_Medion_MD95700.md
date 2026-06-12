---
title: "Problem with Medion MD95700"
date: 2008-05-03
forum: Multimedia Software
---

### Post by DocMAX on 2008-05-03
hello,
i have a nslu2 with debian 4.0 and also a pc with debian 4.0 8both have the same problem). i compiled the latest v4l-dvb drivers and installed the modules. when i connect the Medion MD95700 i get the following syslog:

```
usb 3-1.4.4: new high speed USB device using ehci_hcd and address 6
usb 3-1.4.4: configuration #1 chosen from 1 choice
hub 3-1.4.4:1.0: USB hub found
hub 3-1.4.4:1.0: 4 ports detected
usb 3-1.4.4.1: new high speed USB device using ehci_hcd and address 7
usb 3-1.4.4.1: configuration #1 chosen from 1 choice
usb 3-1.4.4.2: new low speed USB device using ehci_hcd and address 8
usb 3-1.4.4.2: configuration #1 chosen from 1 choice
input: X10 Wireless Technology Inc USB Receiver as /class/input/input1
drivers/usb/input/ati_remote.c: Weird data, len=1 ff 00 00 00 00 00 ...
usbcore: registered new driver ati_remote
drivers/usb/input/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
dvb-usb: found a 'Medion MD95700 (MDUSBTV-HYBRID)' in warm state.
dvb-usb: bulk message failed: -22 (2/-1073542592)
i2c_adapter i2c-1: SMBus Quick command not supported, can't probe for chips
i2c_adapter i2c-1: SMBus Quick command not supported, can't probe for chips
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (Medion MD95700 (MDUSBTV-HYBRID))
drivers/usb/core/message.c: selecting invalid altsetting 6
cxusb: set interface failed
dvb-usb: bulk message failed: -22 (1/-1047552756)
usb 3-1.4.4: USB disconnect, address 6
usb 3-1.4.4.1: USB disconnect, address 7
ati_remote 3-1.4.4.2:1.0: ati_remote_irq_in: usb_submit_urb()=-19
dvb-usb: bulk message failed: -22 (5/-1073537388)
cx22702_readreg: readreg error (ret == -121)
dvb-usb: no frontend was attached by 'Medion MD95700 (MDUSBTV-HYBRID)'
dvb-usb: bulk message failed: -22 (2/-1047552800)
dvb-usb: Medion MD95700 (MDUSBTV-HYBRID) successfully initialized and connected.
dvb-usb: Medion MD95700 (MDUSBTV-HYBRID) successfully deinitialized and disconnected.
usb 3-1.4.4.2: USB disconnect, address 8
usb 3-2: reset high speed USB device using ehci_hcd and address 5
```

does anyone have a clue where the problem is?

regards

---

