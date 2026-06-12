---
title: "USB Wireless network adapter problem"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by Relaxation82 on 2010-04-04
Dear All,

I have a nasty problem concerning an USB wireless network adapter (3G). The manufacturer of the USB dongle is Nokia and the model is CS-15. I use Ubuntu 9.10 with kernel 2.6.31-21-generic (last update today). The nasty part is that the 3G modem is the only network connection available, and now I can't connect to internet (with the computer in question) for updates etc.

It has worked before with no problems (another than the typical problems with 3G modems and Ubuntu 9.10) using wvdial. It just stopped working after a reboot when I was trying to get wvdial to connect automatically to internet as a part of the login process.

Here is the critical part of the output of "tail -f /var/log/syslog" while the USB dongle was inserted to an USB slot (changing the slot doesn't change anthing; slots work properly when a typical USB memory stick is inserted):

```
usb 1-7: new high speed USB device using ehci_hcd and address 5
usb 1-7: configuration #1 chosen from 1 choice
Initializing USB Mass Storage driver...
scsi7 : SCSI emulation for USB Mass Storage devices
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 7:0:0:0: CD-ROM            Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
sr0: scsi3-mmc drive: 0x/0x caddy
Uniform CD-ROM driver Revision: 3.20
sr 7:0:0:0: Attached scsi CD-ROM sr0
sr 7:0:0:0: Attached scsi generic sg2 type 5
sr 7:0:0:0: [sr0] Unhandled sense code
sr 7:0:0:0: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
sr 7:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Info fld=0x0
sr 7:0:0:0: [sr0] Add. Sense: No additional sense information
end_request: I/O error, dev sr0, sector 86688
Buffer I/O error on device sr0, logical block 10836
sr 7:0:0:0: [sr0] Unhandled sense code
sr 7:0:0:0: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
sr 7:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Info fld=0x0
sr 7:0:0:0: [sr0] Add. Sense: No additional sense information
end_request: I/O error, dev sr0, sector 86688
Buffer I/O error on device sr0, logical block 10836
sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Info fld=0x0
sr 7:0:0:0: [sr0] Add. Sense: Logical block address out of range
end_request: I/O error, dev sr0, sector 86696
Buffer I/O error on device sr0, logical block 10837
sr 7:0:0:0: [sr0] Unhandled sense code
sr 7:0:0:0: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
sr 7:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Info fld=0x0
sr 7:0:0:0: [sr0] Add. Sense: No additional sense information
end_request: I/O error, dev sr0, sector 86688
Buffer I/O error on device sr0, logical block 10836
sr 7:0:0:0: [sr0] Unhandled sense code
sr 7:0:0:0: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
sr 7:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Info fld=0x0
sr 7:0:0:0: [sr0] Add. Sense: No additional sense information
end_request: I/O error, dev sr0, sector 86688
sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Info fld=0x0
sr 7:0:0:0: [sr0] Add. Sense: Logical block address out of range
end_request: I/O error, dev sr0, sector 86696
sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Info fld=0x0
sr 7:0:0:0: [sr0] Add. Sense: Logical block address out of range
end_request: I/O error, dev sr0, sector 86696
```

Sorry for the long output; I did remove some of the repeating parts, but this was left.
Here are the changes in "lsusb" due to the inserted 3G modem:

```
Bus 001 Device 005: ID 0421:0610 Nokia Mobile Phones
```

and changes in "ls /dev" due to the inserted 3G modem:

```
cdrom2 cdrom3 dvd2 dvd3 sg2 scd0 sr0
```

When it worked, the 3G modem added a device called "ttyACM0" (or so). And finally, the actual question is whether this is something software or something hardware related (i.e. a broken USB dongle)? If it happens to be something software related, can it be fixed? Please do ask more info, if considered necessary.

Thank You for Your help in advance!

---

### Post by QuintinvR on 2010-09-25
Hey Relaxation82.

I know this is a late reply, but I just got a modem like this one and just figured a fix with the help of some googling et al.

In the case of Kubuntu/Mint KDE you will get a popup that asks you what to do with the CDrom. Just eject it via the menu option given.

In the case of Ubuntu - you need to use the commandline to eject the device:

```
eject cdrom2
```

After that network manager should pick up the modem device and you can install it as you would any other usb 3g modem.

Hope this belated response helps someone.

---

