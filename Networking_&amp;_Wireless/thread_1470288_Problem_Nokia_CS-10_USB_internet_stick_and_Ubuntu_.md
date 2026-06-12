---
title: "Problem: Nokia CS-10 USB internet stick and Ubuntu 10.04"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by Menestrello on 2010-05-02
Hi everybody,
after having trouble with Ubuntu 9.10 (solved with a nice *modemmanager* bug fix by a great user) here we are with the new Lucid Lynx: until now, just to be safe, I am trying my Nokia CS-10 USB stick (for wireless 3g connection) with the Live Ubuntu, and it doesn't even get recognized (no red light or anything else)... here's the log:

```
[  637.872135] usb 2-1: new high speed USB device using ehci_hcd and address 6
[  638.005339] usb 2-1: configuration #1 chosen from 1 choice
[  638.285569] Initializing USB Mass Storage driver...
[  638.285839] scsi6 : SCSI emulation for USB Mass Storage devices
[  638.285939] usbcore: registered new interface driver usb-storage
[  638.285942] USB Mass Storage support registered.
[  638.287006] usb-storage: device found at 6
[  638.287007] usb-storage: waiting for device to settle before scanning
[  643.284348] usb-storage: device scan complete
[  643.284840] scsi 6:0:0:0: CD-ROM            Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
[  643.292275] sr1: scsi3-mmc drive: 0x/0x caddy
[  643.292723] sr 6:0:0:0: Attached scsi CD-ROM sr1
[  643.296160] sr 6:0:0:0: Attached scsi generic sg2 type 5
[  643.310214] sr1: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[  643.310242] sr: Sense Key : Hardware Error [current] 
[  643.310252] sr: Add. Sense: No additional sense information
[  643.418997] sr 6:0:0:0: [sr1] Unhandled sense code
[  643.419004] sr 6:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  643.419014] sr 6:0:0:0: [sr1] Sense Key : Hardware Error [current] 
[  643.419025] Info fld=0x0
[  643.419030] sr 6:0:0:0: [sr1] Add. Sense: No additional sense information
[  643.419041] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 5e 00 00 02 00
[  643.419064] end_request: I/O error, dev sr1, sector 80248
[  643.419073] Buffer I/O error on device sr1, logical block 10031
[  643.423370] sr 6:0:0:0: [sr1] Unhandled sense code
[  643.423376] sr 6:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  643.423384] sr 6:0:0:0: [sr1] Sense Key : Hardware Error [current] 
[  643.423394] Info fld=0x0
[  643.423399] sr 6:0:0:0: [sr1] Add. Sense: No additional sense information
[  643.423410] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 5e 00 00 02 00
[  643.423432] end_request: I/O error, dev sr1, sector 80248
[  643.423440] Buffer I/O error on device sr1, logical block 10031
[  643.427119] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.427128] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.427139] Info fld=0x0
[  643.427143] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.427155] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.427178] end_request: I/O error, dev sr1, sector 80256
[  643.427185] Buffer I/O error on device sr1, logical block 10032
[  643.428255] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.428264] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.428274] Info fld=0x0
[  643.428279] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.428290] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.428313] end_request: I/O error, dev sr1, sector 80256
[  643.428320] Buffer I/O error on device sr1, logical block 10032
[  643.429244] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.429253] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.429263] Info fld=0x0
[  643.429267] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.429279] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.429302] end_request: I/O error, dev sr1, sector 80256
[  643.429309] Buffer I/O error on device sr1, logical block 10032
[  643.430242] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.430251] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.430261] Info fld=0x0
[  643.430266] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.430277] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.430299] end_request: I/O error, dev sr1, sector 80256
[  643.430306] Buffer I/O error on device sr1, logical block 10032
[  643.431242] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.431251] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.431261] Info fld=0x0
[  643.431265] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.431277] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.431299] end_request: I/O error, dev sr1, sector 80256
[  643.431305] Buffer I/O error on device sr1, logical block 10032
[  643.432371] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.432380] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.432390] Info fld=0x0
[  643.432394] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.432406] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.432429] end_request: I/O error, dev sr1, sector 80256
[  643.432436] Buffer I/O error on device sr1, logical block 10032
[  643.433494] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.433503] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.433513] Info fld=0x0
[  643.433517] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.433529] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.433552] end_request: I/O error, dev sr1, sector 80256
[  643.433558] Buffer I/O error on device sr1, logical block 10032
[  643.439743] sr 6:0:0:0: [sr1] Unhandled sense code
[  643.439750] sr 6:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  643.439758] sr 6:0:0:0: [sr1] Sense Key : Hardware Error [current] 
[  643.439768] Info fld=0x0
[  643.439773] sr 6:0:0:0: [sr1] Add. Sense: No additional sense information
[  643.439783] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 5e 00 00 02 00
[  643.439806] end_request: I/O error, dev sr1, sector 80248
[  643.439813] Buffer I/O error on device sr1, logical block 10031
[  643.443368] sr 6:0:0:0: [sr1] Unhandled sense code
[  643.443374] sr 6:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  643.443382] sr 6:0:0:0: [sr1] Sense Key : Hardware Error [current] 
[  643.443392] Info fld=0x0
[  643.443396] sr 6:0:0:0: [sr1] Add. Sense: No additional sense information
[  643.443407] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 5e 00 00 02 00
[  643.443430] end_request: I/O error, dev sr1, sector 80248
[  643.444498] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.444507] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.444517] Info fld=0x0
[  643.444521] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.444534] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.444556] end_request: I/O error, dev sr1, sector 80256
[  643.445493] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.445502] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.445512] Info fld=0x0
[  643.445516] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.445528] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.445550] end_request: I/O error, dev sr1, sector 80256
[  643.446492] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  643.446501] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[  643.446511] Info fld=0x0
[  643.446515] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
[  643.446527] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 4e 60 00 00 02 00
[  643.446549] end_request: I/O error, dev sr1, sector 80256
```Any help is welcome :)

PS: I am pretty newbie, so feel free to ask if you need more info that I can provide :o

---

### Post by psygen on 2010-05-13
I'm read this link bellow and working fine in Ubuntu 10.04

[http://febuntoo.com/ayrton-freeman-araujo-configurando-modem-usb-nokia-cs-10-3g-no-ubuntu.html](http://febuntoo.com/ayrton-freeman-araujo-configurando-modem-usb-nokia-cs-10-3g-no-ubuntu.html)

> 
sudo gedit /etc/udev/rules.d/90-nokia-zerocd.rules

paste the content:

SUBSYSTEMS=="usb", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="060c", ACTION=="add", PROGRAM=="nokia-testcd %M %s{serial}", RUN+="/usr/bin/eject -s %k", OPTIONS+="last_rule"

Save and close.

After

sudo vim /lib/udev/nokia-testcd

paste the content:

#!/bin/sh
# Don't eject if flag in place
if [ -f /etc/udev/nokia-zerocd-noeject ]; then
exit 1
fi
# Extract USB serial into major and minor numbers
minor=`echo $2 | sed 's/.[0-9]*\.//'`
major=`echo $2 | sed 's/\.[0-9]*$//'`
# Compare with current software version
if [ "$major" -gt "0" ] ||  [ "$minor" -gt "10" ]; then
exit 1
fi
# Clean exit on match
exit 0

Save and Close.

Execute the commands:

sudo chmod a+x /lib/udev/nokia-testcd
sudo restart udev
sudo restart network-manager

Connect to stick nokia cs10 and use NM-Applet to connect in your ISP.



---

### Post by Groodles on 2010-05-29
These fixes do indeed work on Lucid (10.04) and enable you to use the standard  Network Manager.  I'm posting this while using my CS-10 (O2 Contract).

Thanks for the link!

---

