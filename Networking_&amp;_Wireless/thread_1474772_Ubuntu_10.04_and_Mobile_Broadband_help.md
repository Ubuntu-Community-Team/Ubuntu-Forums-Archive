---
title: "Ubuntu 10.04 and Mobile Broadband help"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by jupitermoonbeam on 2010-05-06
Hi,

I'm running Ubuntu 10.04 on my netbook and I am trying to get my Orange ZTE MF636 3G+ mobile broadband working.

Actually, about two times it worked and was connected and I was using it.  Though that appears to have been a random and non-recratable event.

```
I tried usb_switchmode but that tells me:
Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 No devices in default mode or class found. Nothing to do. Bye.
```

If I do a dmesg | grep -e "modem" I get:
```
[  159.070707] USB Serial support registered for GSM modem (1-port)
[  159.070881] option 1-1:1.0: GSM modem (1-port) converter detected
[  159.071119] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  159.071185] option 1-1:1.1: GSM modem (1-port) converter detected
[  159.071362] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[  159.071428] option 1-1:1.2: GSM modem (1-port) converter detected
[  159.071611] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[  159.071690] option 1-1:1.4: GSM modem (1-port) converter detected
[  159.071918] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3
```

And if I do lsusb I get:
```
Bus 001 Device 009: ID 19d2:0033 ONDA Communication S.p.A.
```

I do notice that sometimes the device is mounted as a CD.  I've tried ejecting it and it appears to be recognized (i.e the above messages appear in dmesg).

It's really, really confusing.  Reading forums with help has muddled my head even more.  

To be honest I'm really disapointed with Ubuntu on this one.  I thought we'd moved on from this sort of hell.

Please, please help.  I need this for work and if Ubuntu won't do it then I'll have no choice but to ditch to Windoze which I really don't want to do.

---

### Post by alexfish on 2010-05-06
hi

have you tried plugging the device in  after booting up

see what happens

---

### Post by jupitermoonbeam on 2010-05-06
It doesn't seem to matter when I plug it in.  It doesn't work either before turning on or after.  Also tried disconnecting and pluging in a couple of times, that doesn't work either.

Though interestingly when I plug it in the keychain comes up asking for my password so something is happening.

---

### Post by alexfish on 2010-05-06
hi

 when the keyring manager comes up , is this the time you get the connection

or cant you describe further what is happening

also can you do this from the terminal

but first boot the computer without the dongle

Code:
  	 	 	 	 	 	  [B]
[/B] tail -f /var/log/syslog

now plug the dongle in

can you post the outputs of two results , one when you get a connection and one when you can't .

thanks in advance 
alexfish

---

### Post by jupitermoonbeam on 2010-05-07
>> when the keyring manager comes up , is this the time you get the connection
I think that was a red herring.  Something else kicks in a little late after start up.  Just happened to coincide with when I was plugging in.

Here's the logs.  There was a lot of the following noise in there:
```
May  7 09:45:06 peters-netbook wpa_supplicant[919]: No network configuration found for the current AP
May  7 09:45:10 peters-netbook kernel: [  671.989172] wlan0: Trigger new scan to find an IBSS to join
May  7 09:45:14 peters-netbook kernel: [  676.000192] wlan0: Trigger new scan to find an IBSS to join
May  7 09:45:14 peters-netbook kernel: [  676.061076] wlan0: Creating new IBSS network, BSSID 12:00:dd:08:88:0e
```

So I've filtered out all those entries.

First off I plugged in the 3G card and got this:
```
May  7 09:45:35 peters-netbook kernel: [  696.844203] usb 1-1: new high speed USB device using ehci_hcd and address 3
May  7 09:45:35 peters-netbook kernel: [  696.989768] usb 1-1: configuration #1 chosen from 1 choice
May  7 09:45:35 peters-netbook kernel: [  697.085498] Initializing USB Mass Storage driver...
May  7 09:45:35 peters-netbook kernel: [  697.086167] scsi2 : SCSI emulation for USB Mass Storage devices
May  7 09:45:35 peters-netbook kernel: [  697.086894] usb-storage: device found at 3
May  7 09:45:35 peters-netbook kernel: [  697.086906] usb-storage: waiting for device to settle before scanning
May  7 09:45:35 peters-netbook kernel: [  697.086972] usbcore: registered new interface driver usb-storage
May  7 09:45:35 peters-netbook kernel: [  697.087158] USB Mass Storage support registered.May  7 09:45:40 peters-netbook kernel: [  702.085706] usb-storage: device scan complete
May  7 09:45:40 peters-netbook kernel: [  702.087489] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
May  7 09:45:40 peters-netbook kernel: [  702.115834] sr0: scsi-1 drive
May  7 09:45:40 peters-netbook kernel: [  702.115849] Uniform CD-ROM driver Revision: 3.20
May  7 09:45:40 peters-netbook kernel: [  702.117853] sr 2:0:0:0: Attached scsi CD-ROM sr0
May  7 09:45:40 peters-netbook kernel: [  702.122022] sr 2:0:0:0: Attached scsi generic sg1 type 5May  7 09:45:53 peters-netbook kernel: [  714.378567] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.378588] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.378608] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.378617] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.378637] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 60 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.378675] end_request: I/O error, dev sr0, sector 937344
May  7 09:45:53 peters-netbook kernel: [  714.378691] __ratelimit: 9 callbacks suppressed
May  7 09:45:53 peters-netbook kernel: [  714.378703] Buffer I/O error on device sr0, logical block 117168
May  7 09:45:53 peters-netbook kernel: [  714.384596] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.384622] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.384648] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.384659] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.384687] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 60 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.384740] end_request: I/O error, dev sr0, sector 937344
May  7 09:45:53 peters-netbook kernel: [  714.384765] Buffer I/O error on device sr0, logical block 117168
May  7 09:45:53 peters-netbook kernel: [  714.390574] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.390594] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.390614] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.390622] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.390642] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 88 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.390680] end_request: I/O error, dev sr0, sector 937504
May  7 09:45:53 peters-netbook kernel: [  714.390697] Buffer I/O error on device sr0, logical block 117188
May  7 09:45:53 peters-netbook kernel: [  714.398555] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.398575] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.398594] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.398602] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.398622] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 88 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.398659] end_request: I/O error, dev sr0, sector 937504
May  7 09:45:53 peters-netbook kernel: [  714.398675] Buffer I/O error on device sr0, logical block 117188
May  7 09:45:53 peters-netbook kernel: [  714.406564] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.406584] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.406603] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.406611] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.406631] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.406669] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.406685] Buffer I/O error on device sr0, logical block 117189
May  7 09:45:53 peters-netbook kernel: [  714.415557] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.415578] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.415597] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.415605] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.415624] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.415662] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.415678] Buffer I/O error on device sr0, logical block 117189
May  7 09:45:53 peters-netbook kernel: [  714.424702] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.424723] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.424742] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.424750] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.424770] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.424809] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.424825] Buffer I/O error on device sr0, logical block 117189
May  7 09:45:53 peters-netbook kernel: [  714.433558] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.433578] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.433597] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.433605] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.433625] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.433662] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.433678] Buffer I/O error on device sr0, logical block 117189
May  7 09:45:53 peters-netbook kernel: [  714.442484] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.442512] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.442538] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.442550] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.442580] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.442635] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.442659] Buffer I/O error on device sr0, logical block 117189
May  7 09:45:53 peters-netbook kernel: [  714.450834] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.450862] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.450891] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.450903] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.450933] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.450986] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.451010] Buffer I/O error on device sr0, logical block 117189
May  7 09:45:53 peters-netbook kernel: [  714.457336] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.457348] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.457358] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.457362] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.457373] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.457392] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.462579] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.462594] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.462610] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.462616] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.462631] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 7c 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.462662] end_request: I/O error, dev sr0, sector 937456
May  7 09:45:53 peters-netbook kernel: [  714.473121] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.473137] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.473151] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.473157] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.473172] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 88 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.473201] end_request: I/O error, dev sr0, sector 937504
May  7 09:45:53 peters-netbook kernel: [  714.478316] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.478331] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.478344] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.478349] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.478362] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.478387] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.489096] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.489112] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.489127] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.489134] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.489149] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.489179] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.493627] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 09:45:53 peters-netbook kernel: [  714.493643] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May  7 09:45:53 peters-netbook kernel: [  714.493658] Info fld=0x0
May  7 09:45:53 peters-netbook kernel: [  714.493665] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
May  7 09:45:53 peters-netbook kernel: [  714.493680] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 93 8a 00 00 02 00
May  7 09:45:53 peters-netbook kernel: [  714.493710] end_request: I/O error, dev sr0, sector 937512
May  7 09:45:53 peters-netbook kernel: [  714.652152] ISO 9660 Extensions: Microsoft Joliet Level 1
May  7 09:45:53 peters-netbook kernel: [  714.669942] ISOFS: changing to secondary root

```

Then I ejected the CD and got this:
```
May  7 09:46:28 peters-netbook kernel: [  749.945651] usb 1-1: USB disconnect, address 3
May  7 09:46:34 peters-netbook kernel: [  755.321173] usb 1-1: new high speed USB device using ehci_hcd and address 4
May  7 09:46:34 peters-netbook kernel: [  755.465837] usb 1-1: configuration #1 chosen from 1 choice
May  7 09:46:34 peters-netbook kernel: [  755.470937] scsi3 : SCSI emulation for USB Mass Storage devices
May  7 09:46:34 peters-netbook kernel: [  755.472081] usb-storage: device found at 4
May  7 09:46:34 peters-netbook kernel: [  755.472095] usb-storage: waiting for device to settle before scanning
May  7 09:46:34 peters-netbook kernel: [  755.560267] usbcore: registered new interface driver usbserial
May  7 09:46:34 peters-netbook kernel: [  755.561808] USB Serial support registered for generic
May  7 09:46:34 peters-netbook kernel: [  755.562603] usbcore: registered new interface driver usbserial_generic
May  7 09:46:34 peters-netbook kernel: [  755.562621] usbserial: USB Serial Driver core
May  7 09:46:34 peters-netbook kernel: [  755.577581] USB Serial support registered for GSM modem (1-port)
May  7 09:46:34 peters-netbook kernel: [  755.579918] option 1-1:1.0: GSM modem (1-port) converter detected
May  7 09:46:34 peters-netbook kernel: [  755.580635] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
May  7 09:46:34 peters-netbook kernel: [  755.580721] option 1-1:1.1: GSM modem (1-port) converter detected
May  7 09:46:34 peters-netbook kernel: [  755.584112] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
May  7 09:46:34 peters-netbook kernel: [  755.584199] option 1-1:1.2: GSM modem (1-port) converter detected
May  7 09:46:34 peters-netbook kernel: [  755.584729] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
May  7 09:46:34 peters-netbook kernel: [  755.584826] option 1-1:1.4: GSM modem (1-port) converter detected
May  7 09:46:34 peters-netbook kernel: [  755.586891] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3
May  7 09:46:34 peters-netbook kernel: [  755.587099] usbcore: registered new interface driver option
May  7 09:46:34 peters-netbook kernel: [  755.587107] option: v0.7.2:USB Driver for GSM modems
May  7 09:46:34 peters-netbook modem-manager: (ttyUSB1) opening serial device...May  7 09:46:39 peters-netbook kernel: [  760.694805] usb-storage: device scan complete
May  7 09:46:39 peters-netbook kernel: [  760.696758] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
May  7 09:46:39 peters-netbook kernel: [  760.703207] sd 3:0:0:0: Attached scsi generic sg1 type 0
May  7 09:46:39 peters-netbook kernel: [  760.726467] sd 3:0:0:0: [sdb] Attached SCSI removable diskMay  7 09:46:49 peters-netbook modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'May  7 09:46:54 peters-netbook modem-manager: (ttyUSB2) opening serial device...
May  7 09:47:09 peters-netbook modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'May  7 09:47:24 peters-netbook modem-manager: (ttyUSB0) opening serial device...
May  7 09:47:39 peters-netbook modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
May  7 09:47:45 peters-netbook modem-manager: (ttyUSB3) opening serial device...
May  7 09:47:45 peters-netbook modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
May  7 09:47:56 peters-netbook modem-manager: (ttyUSB1) closing serial device...
May  7 09:48:01 peters-netbook modem-manager: (ttyUSB2) closing serial device...May  7 09:48:06 peters-netbook modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 claimed port ttyUSB1
May  7 09:48:06 peters-netbook modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1
May  7 09:48:06 peters-netbook modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 as /org/freedesktop/ModemManager/Modems/0
May  7 09:48:06 peters-netbook modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 claimed port ttyUSB2
May  7 09:48:06 peters-netbook modem-manager: (ttyUSB3) closing serial device...
May  7 09:48:07 peters-netbook modem-manager: mm_modem_base_add_port: assertion `port == NULL' failed
May  7 09:48:07 peters-netbook modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1
May  7 09:48:07 peters-netbook modem-manager: do_grab_port: plugin 'ZTE' claimed to support tty/ttyUSB3 but couldn't: (-1) (unknown)
May  7 09:48:07 peters-netbook NetworkManager: Could not get device: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't existMay  7 09:48:19 peters-netbook modem-manager: (ttyUSB0) closing serial device...May  7 09:48:46 peters-netbook NetworkManager: <info>  Sleeping...
May  7 09:48:46 peters-netbook NetworkManager: <info>  (eth0): now unmanaged
May  7 09:48:46 peters-netbook NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
May  7 09:48:46 peters-netbook NetworkManager: <info>  (eth0): cleaning up...
May  7 09:48:46 peters-netbook NetworkManager: <info>  (eth0): taking down device.
May  7 09:48:46 peters-netbook NetworkManager: <info>  (wlan0): now unmanaged
May  7 09:48:46 peters-netbook NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 37)
May  7 09:48:46 peters-netbook NetworkManager: <info>  (wlan0): cleaning up...
May  7 09:48:46 peters-netbook NetworkManager: <info>  (wlan0): taking down device.
May  7 09:48:47 peters-netbook avahi-daemon[723]: Withdrawing address record for fe80::222:69ff:fe0b:f37 on wlan0.
May  7 09:48:47 peters-netbook wpa_supplicant[919]: Failed to disable WPA in the driver.
May  7 09:48:54 peters-netbook NetworkManager: <info>  Waking up...
May  7 09:48:54 peters-netbook NetworkManager: <info>  (eth0): now managed
May  7 09:48:54 peters-netbook NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  7 09:48:54 peters-netbook NetworkManager: <info>  (eth0): bringing up device.
May  7 09:48:54 peters-netbook kernel: [  895.554772] r8169: eth0: link down
May  7 09:48:54 peters-netbook kernel: [  895.555970] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  7 09:48:54 peters-netbook NetworkManager: <info>  (eth0): preparing device.
May  7 09:48:54 peters-netbook NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  7 09:48:54 peters-netbook NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May  7 09:48:54 peters-netbook NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May  7 09:48:54 peters-netbook NetworkManager: <info>  (wlan0): now managed
May  7 09:48:54 peters-netbook NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
May  7 09:48:54 peters-netbook NetworkManager: <info>  (wlan0): bringing up device.May  7 09:48:54 peters-netbook NetworkManager: <info>  (wlan0): preparing device.
May  7 09:48:54 peters-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
May  7 09:48:54 peters-netbook NetworkManager: <WARN>  nm_device_wifi_set_mode(): error setting card wlan0 to mode 2: Device or resource busy
May  7 09:48:54 peters-netbook kernel: [  895.844685] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  7 09:48:54 peters-netbook NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
May  7 09:48:54 peters-netbook NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
May  7 09:48:54 peters-netbook wpa_supplicant[919]: WPS-AP-AVAILABLE 
May  7 09:48:54 peters-netbook wpa_supplicant[919]: Failed to initiate AP scan.
May  7 09:48:55 peters-netbook wpa_supplicant[919]: WPS-AP-AVAILABLE 
May  7 09:49:16 peters-netbook wpa_supplicant[919]: WPS-AP-AVAILABLE 
May  7 09:49:31 peters-netbook kernel: [  932.838268] usb 1-1: USB disconnect, address 4
May  7 09:49:31 peters-netbook kernel: [  932.838407] option: option_instat_callback: error -108
May  7 09:49:31 peters-netbook kernel: [  932.838944] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
May  7 09:49:31 peters-netbook kernel: [  932.839031] option 1-1:1.0: device disconnected
May  7 09:49:31 peters-netbook kernel: [  932.839483] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
May  7 09:49:31 peters-netbook kernel: [  932.839561] option 1-1:1.1: device disconnected
May  7 09:49:31 peters-netbook kernel: [  932.840000] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
May  7 09:49:31 peters-netbook kernel: [  932.840075] option 1-1:1.2: device disconnected
May  7 09:49:31 peters-netbook kernel: [  932.869429] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
May  7 09:49:31 peters-netbook kernel: [  932.869499] option 1-1:1.4: device disconnected
May  7 09:49:42 peters-netbook kernel: [  943.387135] r8169: eth0: link up
May  7 09:49:42 peters-netbook kernel: [  943.387929] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  7 09:49:42 peters-netbook NetworkManager: <info>  (eth0): carrier now ON (device state 2)
May  7 09:49:42 peters-netbook NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
May  7 09:49:42 peters-netbook NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May  7 09:49:42 peters-netbook NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May  7 09:49:42 peters-netbook NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
May  7 09:49:42 peters-netbook NetworkManager: <info>  dhclient started with pid 1929
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
May  7 09:49:42 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
May  7 09:49:42 peters-netbook dhclient: Internet Systems Consortium DHCP Client V3.1.3
May  7 09:49:42 peters-netbook dhclient: Copyright 2004-2009 Internet Systems Consortium.
May  7 09:49:42 peters-netbook dhclient: All rights reserved.
May  7 09:49:42 peters-netbook dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  7 09:49:42 peters-netbook dhclient: 
May  7 09:49:42 peters-netbook NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
May  7 09:49:42 peters-netbook dhclient: Listening on LPF/eth0/00:1e:68:b7:95:f4
May  7 09:49:42 peters-netbook dhclient: Sending on   LPF/eth0/00:1e:68:b7:95:f4
May  7 09:49:42 peters-netbook dhclient: Sending on   Socket/fallback
May  7 09:49:43 peters-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  7 09:49:43 peters-netbook dhclient: DHCPOFFER of 10.3.30.2 from 10.3.30.248
May  7 09:49:43 peters-netbook dhclient: DHCPREQUEST of 10.3.30.2 on eth0 to 255.255.255.255 port 67
May  7 09:49:43 peters-netbook dhclient: DHCPACK of 10.3.30.2 from 10.3.30.248
May  7 09:49:43 peters-netbook dhclient: bound to 10.3.30.2 -- renewal in 189036 seconds.
May  7 09:49:43 peters-netbook NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
May  7 09:49:43 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  7 09:49:43 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
May  7 09:49:43 peters-netbook NetworkManager: <info>    address 10.3.30.2
May  7 09:49:43 peters-netbook NetworkManager: <info>    prefix 23 (255.255.254.0)
May  7 09:49:43 peters-netbook NetworkManager: <info>    gateway 10.3.30.252
May  7 09:49:43 peters-netbook NetworkManager: <info>    nameserver '10.5.1.1'
May  7 09:49:43 peters-netbook NetworkManager: <info>    nameserver '10.5.1.2'
May  7 09:49:43 peters-netbook NetworkManager: <info>    wins '10.5.1.1'
May  7 09:49:43 peters-netbook NetworkManager: <info>    wins '10.5.1.2'
May  7 09:49:43 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
May  7 09:49:43 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
May  7 09:49:43 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
May  7 09:49:43 peters-netbook avahi-daemon[723]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.3.30.2.
May  7 09:49:43 peters-netbook avahi-daemon[723]: New relevant interface eth0.IPv4 for mDNS.
May  7 09:49:43 peters-netbook avahi-daemon[723]: Registering new address record for 10.3.30.2 on eth0.IPv4.
May  7 09:49:44 peters-netbook NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
May  7 09:49:44 peters-netbook NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
May  7 09:49:44 peters-netbook NetworkManager: <info>  Activation (eth0) successful, device activated.
May  7 09:49:44 peters-netbook NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
May  7 09:49:44 peters-netbook avahi-daemon[723]: Registering new address record for fe80::21e:68ff:feb7:95f4 on eth0.*.
May  7 09:49:42 peters-netbook ntpdate[1984]: step time server 91.189.94.4 offset -1.779774 sec
May  7 09:49:51 peters-netbook kernel: [  954.380103] eth0: no IPv6 routers present
May  7 09:50:26 peters-netbook wpa_supplicant[919]: WPS-AP-AVAILABLE 

```

---

### Post by alexfish on 2010-05-07
hi

if you want to use Mobile broadband connection ,disable wireless and cable connection

as they will override the gsm connection and place the server addresses in the ett/resolv.conf 

do the above see what happens

---

### Post by jupitermoonbeam on 2010-05-07
I disabled Wireless through the applet.  There isn't an option to disable cabled connection (though it wasn't plugged in).  Tried just the 'Disable Networking' option.

Didn't work.

---

### Post by alexfish on 2010-05-08
hi

I have a zte device and at boot time the system is trying to access the device then boot screen will come up with errors, as to what is actually happening I could only guess,different devices are throwing up different errors ,you are not alone ,you have one advantage it does work most of the time.

here is what I would do at present.if you the device configures best when connected after boot then do so.

as time goes by people will be reporting bug's and updates may be in the pipe line,

my update notifier has just popped up , I am going to update my system and see what happens, 

Can I ask which Kernel version are you using , then when I have updated will let you know the out come .

regards

alexfish

---

### Post by jrjoew on 2010-05-08
I don't know if any of this will help, but I am using the Verizon USB 760 for mobile broadband.  I had to change the code in /etc/udev/rules.d/70-persistent-cd.rules to add this code: 
   RUN+="/usr/bin/eject %k"
Tack this on to the end of any line that calls for Mass_Storage Device. 

Then the following code was added to /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi

<!-- Verizon USB760 -->   Your device may be different. 
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command.sets" type="strlist">IS707-A</append>
</match>
</match>
</match>

This code does work for the Verizon USB 760.  I am on a Gateway NV54, 250Gb, 4Gb RAM. 
If this does not help, perhaps it will spark something and the correct codes can be found for the devices that you are all using...  

Hope this does some good.  Works for me fine.  

Thanks.  Joe

---

### Post by pdc on 2010-05-08
like alex, I have an MF636; and I find with 10.04 it flips automatically, and I can select and dial with it;

 jupitermoonbeam:

ubuntu has a USB startup disk creator programme: in system, administration?????

what about copying the 10.04 .iso onto a USB spare stick: even a 1G would do ...... so that is the input file;

......... *or whatever you need to do to tell the programme where to get the .iso* ..........

... you must still have a 10.04 iso still

and you get the system to burn it out onto another USB stick: say a 2G stick;


then you get a live (and persistent) usb boot disk for 10.04 ..

then (F2?) make sure your boot sequence allows to boot from that usb stick;

and boot from there: see if your MF636 will be recognised; if it is like mine, it seems to auto-flip; and be ready for configuration 

.... there have been a number of posts where people have problems, ........ strange problems ......... and post back finally that on a reinstallation, all their problems are solved 

... I have a hunch that may be your solution but can I suggest you try the above first?

and I haven't ever needed to install usb_modeswitch with 10.04 ............

---

### Post by alexfish on 2010-05-09
Hi

one way to switch off the massstorage/cd is to disable with an AT command

AT+ZCDRUN=8

this works on a zte 626 may work with others ,but you have to find the correct control line have done this through a serial port terminal ,using tttyUSB1

the response was this

OK 
AT+ZCDRUN=8  
Close autorun state result(0:FAIL 1:SUCCESS):1 


to turn it back on again

AT+ZCDRUN=9.

---

### Post by tlee on 2010-05-11
Greetings--

I've been having a similar problem.  My modem is a Huawei E220.

I found that selecting the previous kernel version (...21) from the boot menu allowed me to connect without any problems.  It's not really a solution, but it will work in the meantime.

Also, I notice from the output of dmesg that, even as it works now, it is recognized as a CD-ROM.  This doesn't seem to affect the functioning of the modem.


Best,

tlee

---

### Post by crunchfighter on 2010-05-11
Working 10.4 upgrade here.  New USB Velocity antenna from AT&T.

How are you getting it to actually connect?  I have my USB antenna plugged in, the Network Connections Mobile Broadband tab shows my connection read to go ("never used").  I cannot find an option to say "connect to this device now". 

I tried auto connect with no luck.

I'm sure I'm missing something easy here.  Any thoughts?

---

### Post by alexfish on 2010-05-11
> **crunchfighter said:**
> Working 10.4 upgrade here.  New USB Velocity antenna from AT&T.

How are you getting it to actually connect?  I have my USB antenna plugged in, the Network Connections Mobile Broadband tab shows my connection read to go ("never used").  I cannot find an option to say "connect to this device now". 

I tried auto connect with no luck.

I'm sure I'm missing something easy here.  Any thoughts?

hi

try to see if the device is configured as a modem and also the ports it is using and post the results 

code:

dmesg | grep -e "modem" -e "tty" 


if network manager is not recognising the device or can't configure the connection then you could try wvdial or gnome ppp which is a front end to wvdial

---

### Post by foresthill on 2010-05-11
If you have a dual boot system, get the device working in Windows, then immediately reboot into 10.4.

Sounds as if the device has not been flipped and 10.4 is recognizing it as a flash drive rather than a modem. Flipping it in Windows using the manufacturer's software, then rebooting will provide a temporary workaround until you can install usb_modeswitch from Synaptics (run Update Manager first).

Since you have "connect automatically" selected, you'll know right away if the problem is solved because you'll see the network manager icon trying to connect.

At least this is how I was able to get my Cricket A600 wireless broadband modem to work, your mileage may vary, but it's my understanding that all of the USB 3G modems need to be flipped, and doing it in Windows solve the problem, at least until you shut the system down and the modem "unflips".

---

### Post by crunchfighter on 2010-05-12
> **alexfish said:**
> hi

try to see if the device is configured as a modem and also the ports it is using and post the results 

code:

dmesg | grep -e "modem" -e "tty" 


if network manager is not recognising the device or can't configure the connection then you could try wvdial or gnome ppp which is a front end to wvdial

Thanks for the tip.  I'm not actually with that machine right now, so I'll get back to you shortly...

---

### Post by crunchfighter on 2010-05-12
> **foresthill said:**
> If you have a dual boot system, get the device working in Windows, then immediately reboot into 10.4.

Sounds as if the device has not been flipped and 10.4 is recognizing it as a flash drive rather than a modem. Flipping it in Windows using the manufacturer's software, then rebooting will provide a temporary workaround until you can install usb_modeswitch from Synaptics (run Update Manager first).

Since you have "connect automatically" selected, you'll know right away if the problem is solved because you'll see the network manager icon trying to connect.

At least this is how I was able to get my Cricket A600 wireless broadband modem to work, your mileage may vary, but it's my understanding that all of the USB 3G modems need to be flipped, and doing it in Windows solve the problem, at least until you shut the system down and the modem "unflips".

I did get it to work in windows vista, but 10.4 recognizes it as "CD Zero" and doesn't give me the option to connect.  I'll work on the other technique posted yesterday and get back to the board shortly.
Thanks.

---

### Post by crunchfighter on 2010-05-15
> **alexfish said:**
> hi

try to see if the device is configured as a modem and also the ports it is using and post the results 

code:

dmesg | grep -e "modem" -e "tty" 


if network manager is not recognising the device or can't configure the connection then you could try wvdial or gnome ppp which is a front end to wvdial

Here are the results:
craig@craig-gateway:~$ dmesg | grep -e "modem" -e "tty" 
[    0.000000] console [tty0] enabled
[    0.416177] tty tty14: hash matches
craig@craig-gateway:~$ 

Not sure if that output means it is recognizing the device or not.

---

### Post by crunchfighter on 2010-05-15
Just played with gnome ppp, it is not "detecting" my modem.  I tried cycling through all the devices on the setup menu including the non-USB options with no luck.

I also tried this after seeing it on another thread:
craig@craig-gateway:~$ sudo wvdial /etc/wvdial.conf
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
craig@craig-gateway:~$

---

### Post by foresthill on 2010-05-15
Is it still listed as a USB drive? If so, then it hasn't been flipped.

---

### Post by crunchfighter on 2010-05-15
> **foresthill said:**
> Is it still listed as a USB drive? If so, then it hasn't been flipped.

Photo attached of what it sees it as. -> ZeroCD  ?

I've tried going back and forth to windows.  Works fine in windows.  It's powered in Linux with the lights on, but no action.  Puzzling.

---

### Post by foresthill on 2010-05-15
And you have usb-modeswitch installed?

---

### Post by crunchfighter on 2010-05-15
> **foresthill said:**
> And you have usb-modeswitch installed?

hmmmm...  don't know.  I'll have to look at that.  Is it part of a new install?

---

### Post by foresthill on 2010-05-15
No, it's not, you have to install it manually. Here is the command, if you have a working internet connection:

[PHP]sudo apt-get install usb-modeswitch [/PHP]

---

### Post by alexfish on 2010-05-15
> **crunchfighter said:**
> Photo attached of what it sees it as. -> ZeroCD  ?

I've tried going back and forth to windows.  Works fine in windows.  It's powered in Linux with the lights on, but no action.  Puzzling.

hi

try right click on the zerocd on your desk top and select eject from the mouse menu, then see what happens

use the below code from the terminal  to if anything changes

code:

dmesg | grep -e "modem" -e "tty"

---

### Post by crunchfighter on 2010-05-15
> **alexfish said:**
> hi

try right click on the zerocd on your desk top and select eject from the mouse menu, then see what happens

use the below code from the terminal  to if anything changes

code:

dmesg | grep -e "modem" -e "tty"

It went away from the desktop.  Light on modem still on.
craig@craig-gateway:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.416177] tty tty14: hash matches
craig@craig-gateway:~$

---

### Post by crunchfighter on 2010-05-15
> **foresthill said:**
> No, it's not, you have to install it manually. Here is the command, if you have a working internet connection:

[PHP]sudo apt-get install usb-modeswitch [/PHP]

Installed.  I'm not seeing much change...still researching if there is more I need to do.

---

### Post by crunchfighter on 2010-05-15
Tried a reboot too...

---

### Post by alexfish on 2010-05-15
Hi

possibly a different device as the OP

can you post the details of this command from the terminal

code:

lsusb

thanks in advance 

alexfish

---

### Post by crunchfighter on 2010-05-15
> **alexfish said:**
> Hi

possibly a different device as the OP

can you post the details of this command from the terminal

code:

lsusb

thanks in advance 

alexfish


craig@craig-gateway:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0af0:7a05 Option 
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
craig@craig-gateway:~$ 



I'm trying to go through this site right now as well: [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by crunchfighter on 2010-05-15
> **crunchfighter said:**
> craig@craig-gateway:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0af0:7a05 Option 
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
craig@craig-gateway:~$ 



This should be the USB antenna: Bus 002 Device 004: ID 0af0:7a05 Option

It's an AT&T Velocity device which is manufactured by Option.

---

### Post by alexfish on 2010-05-15
hi 

can't find a listing for the device in usb-mode switch

can you try this from the terminal

Code:

sudo modprobe usbserial vendor=0x0af0 product=0x7a05

then:

dmesg | grep -e "modem" -e "tty"

---

### Post by crunchfighter on 2010-05-15
craig@craig-gateway:~$ sudo modprobe usbserial vendor=0X0af0 product=0x7a05
[sudo] password for craig: 
craig@craig-gateway:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
craig@craig-gateway:~$

---

### Post by crunchfighter on 2010-05-15
I'm reading this:
> All Option devices
All known Option devices use the USB storage command REZERO UNIT for switching (inherited from SCSI). Older devices change vendor and product ID, newer ones don't (just their device class). These newer sticks have a special interface after switching (HSO) for which there is a specific driver. Some older devices are able to be loaded with the new HSO firmware which changes their behaviour.
Note: for HSO driver questions and HowTos consult the fine Pharscape site!
All Option devices come included in the config database of the new integrated version. There is no need to use "ozerocdoff" or "rezero" anymore.
There is a switching routine for Option devices in the kernel driver usb-storage (since beginning of 2009). It works only for devices entered in "unusual_devs.h". More to that below.
You can safely install USB_ModeSwitch alongside. If your Option device gets switched by the kernel it just does nothing, otherwise it kicks in. 

Then this:

> In case of trouble, look into "unusual_devs.h" in the "drivers/usb/storage" folder of your kernel source. If your default ID (vendor and product ID of the storage part) can be found there and you get errors when running USB_ModeSwitch, try first to blacklist "usb-storage".

I'm not getting any errors I see, I just see nothing.  Possible that it's just so new that USB_ModeSwitch doesn't support yet?

---

### Post by alexfish on 2010-05-15
hi

the option device may need the hsolink , have a look in the repos 

see what happens

regards

alexfish

---

### Post by crunchfighter on 2010-05-15
I'll do that.  Thanks for all the help.

---

### Post by alexfish on 2010-05-15
hi again

you may also need resolv.conf from the repos 

did a post a while a go but referenced to option icon as sold by orange

the original hso drivers had to be updated ; but can't confirm as to 10.04

if you have a problem then try the  [Pharscape]("http://www.pharscape.org/") site!

regards

alexfish

---

### Post by crunchfighter on 2010-05-15
I'm working through the Pharscape site right now.  My device is new enough that he has not yet posted anything on it.

---

### Post by pdc on 2010-05-15
I was interested to see the ID that you got 

> Bus 002 Device 004: ID 0af0:7a05 Option

because if you look at the usb_modeswitch config file, 

[http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup)

device ID that you list

> 0af0

is the TargetVendor, not the Default Vendor, so it seems your device has switched .........

I just wonder if it is new and the Message Content is different 

eg here is one option device from the usb_modeswitch file

>  Option GlobeSurfer Icon 7.2 
#
# Contributor: The Pharscape Forum

;*DefaultVendor*=  *0x05c6*
;DefaultProduct= 0x1000

;**TargetVendor**=   **0x0af0**
;TargetProduct=  0x6901

# only for reference and 0.x versions
# MessageEndpoint=0x05

;**MessageContent**="55534243123456780000000000000601000000000000000000000000000000"



so where usb_modeswitch says you don't need ozerocdoff installed, I just wonder if you should go ahead and install it from where alex, who knows a huge lot about this stuff, recommends .............

but 

> My device is new enough that he has not yet posted anything on it.

so that may thwart you again: 

if you join the usb_modeswitch forum, 

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

josh is incredibly good at helping and you could help him a lot by identifying details of your device to add to the knowledge

---

### Post by alexfish on 2010-05-15
hi
may be  it will just be the ids to change

have a look at this thread

[SOLVED] [Re: Option iCON 515m wireless USB modem  (Orange)]("http://ubuntuforums.org/showthread.php?t=1351612") ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG] [1]("http://ubuntuforums.org/showthread.php?t=1351612") [2]("http://ubuntuforums.org/showthread.php?t=1351612&page=2"))

read through it before you commit , as you say it is a new device

but I would also recommend following the how to, etc , at the Pharscape site

added ; just out of interest is there any info on the CD that appeared on the desk top; probably got win drivers on board , anything on linux?

regards

alexfish

---

### Post by crunchfighter on 2010-05-15
I discovered I was wrong.  There is a driver he posted that I just donwloaded.  I'm wading through the readme file now to see what I need to do.  He reports success with this device, so I have no excuse.

I'll report back with success shortly...at least, that's the plan...

---

### Post by pdc on 2010-05-15
great! good luck

I see your device 

> New **USB Velocity antenna from AT&T**.

has its own page on pharscape, complete with photos of the device; ... even describes how to get GPS going on it ..

[http://pharscape.org/att-velocity-gps-and-linux.html](http://pharscape.org/att-velocity-gps-and-linux.html)

as Paul describes it 

[http://www.peck.org.uk/forum/index.php/topic,827.0.html](http://www.peck.org.uk/forum/index.php/topic,827.0.html)

if you upgrade kernel to 2.6.33 the device works OOTB ...

if using kernel 2.6.31 he says

> If, like me, you are using a distribution that has a kernel version between 2.6.27 and 2.6.33 then you can use my unofficial modified driver that is attached to this message.

and he has has driver on that page for one to download and install (a tar.gz file)

If one wanted to upgrade to a newer kernel, eg the 2.6.34 dionblundell provided an excellent howto in post #31 here

[http://ubuntuforums.org/showthread.php?p=9299212#post9299212](http://ubuntuforums.org/showthread.php?p=9299212#post9299212)

---

