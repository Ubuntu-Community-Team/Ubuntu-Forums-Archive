---
title: "USB TV Tuner - analogue tuner doesn't work"
date: 2009-12-27
forum: Multimedia Software
---

### Post by misiu369 on 2009-12-27
Hi, I've been searching for a couple of days now and still no luck.
I've got Medion MD95700 USB TV tuner. It's a hybrid and the DVB part works great. The problem's that where I live, the signal is still analogue, so I need the other part of it to work as well.

Let me make this clear - the DVB tuner works. 
I need to make the analogue part working.

I found this page:
[http://www.linuxtv.org/wiki/index.php/Medion_MD95700_%28DVB-T%29](http://www.linuxtv.org/wiki/index.php/Medion_MD95700_%28DVB-T%29)> The analogue part seems to be handled by a Conexant CX25842. It's kernel driver is cx25840, although the main driver for the Box isn't finished so it doesn't get detected (on 2.6.32). but I don't really understand what it says - does that mean it should or shouldn't work? Does this suggest any way to make it work?

Here's what shows up in **lsusb** after plugging it in:
```
Bus 001 Device 020: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 021: ID 1660:0932 Creatix Polymedia GmbH 
Bus 001 Device 022: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
```
First one is a built-in usb hub, second is the tv tuner, third is a IR receiver.

Here's **dmesg** from when I plug it in:
```
[53263.590098] usb 1-5: new high speed USB device using ehci_hcd and address 20
[53263.741251] usb 1-5: configuration #1 chosen from 1 choice
[53263.744180] hub 1-5:1.0: USB hub found
[53263.744955] hub 1-5:1.0: 4 ports detected
[53264.023888] usb 1-5.1: new high speed USB device using ehci_hcd and address 21
[53264.131908] usb 1-5.1: config 1 interface 0 altsetting 6 bulk endpoint 0x82 has invalid maxpacket 188
[53264.132706] usb 1-5.1: configuration #1 chosen from 1 choice
[53264.198839] dvb-usb: found a 'Medion MD95700 (MDUSBTV-HYBRID)' in warm state.
[53264.201848] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[53264.258960] DVB: registering new adapter (Medion MD95700 (MDUSBTV-HYBRID))
[53266.261519] dvb-usb: recv bulk message failed: -110
[53266.263226] DVB: registering adapter 0 frontend 0 (Conexant CX22702 DVB-T)...
[53266.288068] tuner-simple 1-0061: creating new instance
[53266.288074] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[53266.288436] dvb-usb: Medion MD95700 (MDUSBTV-HYBRID) successfully initialized and connected.
[53266.361987] usb 1-5.2: new low speed USB device using ehci_hcd and address 22
[53266.478702] usb 1-5.2: configuration #1 chosen from 1 choice
[53266.507529] input: X10 Wireless Technology Inc USB Receiver as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5.2/input/input23
```

Attachments:
```
- screenshots of the device manager 
--- the tv tuner device
--- the interface that probably is the analogue tuner
- text files
--- lsusb -v (of the 3 devices)
--- lsmod
```

---

### Post by misiu369 on 2009-12-30
bump!

---

### Post by misiu369 on 2010-01-02
bumpity bump!

---

### Post by misiu369 on 2010-01-31
bump bump and away!

---

