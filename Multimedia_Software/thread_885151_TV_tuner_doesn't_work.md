---
title: "TV tuner doesn't work"
date: 2008-08-09
forum: Multimedia Software
---

### Post by Karolaq on 2008-08-09
Hello!
I have Medion 95700 TV tuner. It's based on saa7134.
I loaded saa7134 module but /dev/video0 didn't appear.

dmesg:
```
[16867.643055] usb 2-2: USB disconnect, address 4
[16867.643059] usb 2-2.1: USB disconnect, address 5
[16867.643422] dvb-usb: Medion MD95700 (MDUSBTV-HYBRID) successfully deinitialized and disconnected.
[16867.643559] usb 2-2.2: USB disconnect, address 6
[16870.650814] usb 2-2: new high speed USB device using ehci_hcd and address 7
[16870.783861] usb 2-2: configuration #1 chosen from 1 choice
[16870.784250] hub 2-2:1.0: USB hub found
[16870.784436] hub 2-2:1.0: 4 ports detected
[16871.106894] usb 2-2.1: new high speed USB device using ehci_hcd and address 8
[16871.199438] usb 2-2.1: configuration #1 chosen from 1 choice
[16871.256919] dvb-usb: found a 'Medion MD95700 (MDUSBTV-HYBRID)' in warm state.
[16871.257683] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[16871.314903] DVB: registering new adapter (Medion MD95700 (MDUSBTV-HYBRID))

```

lsusb:
```
Bus 002 Device 009: ID 0bc7:0006 X10 Wireless Technology, Inc. 
Bus 002 Device 008: ID 1660:0932  
Bus 002 Device 007: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"

```

What should I do?

---

### Post by rydz on 2009-05-04
Hi,
I've a problem with TV card: Medion md95700
The problem is my Ubuntu can't se analog card (Md95700 is hybrid card, both analog and digital).
On the page: [http://www.linuxtv.org/wiki/index.php/Medion_MD95700_(DVB-T](http://www.linuxtv.org/wiki/index.php/Medion_MD95700_(DVB-T)) I read that the module responsible for analog support is called cx25840.
Unfortunatelly after loading it nothing happens in dmesg. (nothing new was found)
In /dev there is no /dev/video1 (on video0 I've got webcam)

After connecting the card to the computer there are some modules being loaded, as u can see in dmesg:
```
[  161.745990] dvb-usb: found a 'Medion MD95700 (MDUSBTV-HYBRID)' in warm state.
[  161.746004] >>> de 00 
[  161.746286] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  161.803631] DVB: registering new adapter (Medion MD95700 (MDUSBTV-HYBRID))
[  161.804790] >>> 51 
[  163.804219] dvb-usb: recv bulk message failed: -110
[  163.804421] >>> 09 01 01 63 1f 
[  163.805063] <<< 08 03 
[  163.805074] DVB: registering adapter 0 frontend 1 (Conexant CX22702 DVB-T)...
[  163.805372] >>> 09 01 01 63 0d 
[  163.806063] <<< 08 00 
[  163.806073] >>> 08 63 02 0d 00 
[  163.806559] <<< 08 
[  163.806566] >>> 0e 02 01 
[  163.806807] <<< 01 
[  163.806813] >>> 09 00 01 61 
[  163.807165] <<< 08 34 
[  163.807173] >>> 0e 02 00 
[  163.807415] <<< 01 
[  163.807420] >>> 09 01 01 63 0d 
[  163.813955] <<< 08 00 
[  163.813969] >>> 08 63 02 0d 01 
[  163.814438] <<< 08 
[  163.814448] tuner-simple 0-0061: creating new instance
[  163.814454] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[  163.814810] >>> dc 00 
[  163.814929] dvb-usb: Medion MD95700 (MDUSBTV-HYBRID) successfully initialized and connected.
[  163.814990] usbcore: registered new interface driver dvb_usb_cxusb
```

As u can see there is error: "[  163.804219] dvb-usb: recv bulk message failed: -110"
and I'm wondering if it may be the reason that the analog tv is not working.

Results of lsusb:
```

Bus 002 Device 004: ID 064e:c107 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15d9:0a33 Unknown 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 001 Device 003: ID 1660:0932 Creatix Polymedia GmbH 
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

