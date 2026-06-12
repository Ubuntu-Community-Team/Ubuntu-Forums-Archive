---
title: "ZTE MF112 - broadband has stopped working"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by taryneast on 2011-10-17
So... 21 days ago, my wireless broadband was working just fine. Then I went to Budapest and borrowed myself a second dongle to use there. I remember I had to play around with usb_modeswitch-data and installed betavine to make it work...

Now I'm back home again and it seems my old dongle no longer works, so I no longer have access anymore.

I have tried:
- reinstalling usb-modeswitch and usb-modeswitch-data
- reinstalling wvdial
- updating /etc/udev/rules.d/40-ttyUSB.rules to add:
 KERNEL=="ttyUSB1", ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0031", NAME="ttyUSB0"
KERNEL=="ttyUSB0", ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0031", NAME="ttyUSB1"
- updating /etc/udev/rules.d/zte_eject.rules to add:
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0103", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"


What happens so far:
- I plug the dongle in
- after a few minutes it correctly flips from 19d2:0103 to 19d2:0031
- the following lines happily show up in dmesg:
[ 2432.218238] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[ 2432.218382] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[ 2432.229890] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2


BUT... the device never appears in the list in network-manager...
so I can't ever connect - or set up a new connection-manager profile (not that I need to, the old one used to work fine). It makes no difference if I eject or not anymore, it still doesn't show up as a device in network manager.
But there are some other odd messages in dmesg (see listing way below).

I can confirm that the dongle still works just fine as it connects when I'm on my Mac partition. It's just not showing up as a device in network-manager.

I even tried calling around local "linux support" places in London... but it seems nobody actually supports this kind of thing (I'd pay!)

Can anybody here help?



dmesg listing:
[ 3299.808037] usb 2-4: new high speed USB device using ehci_hcd and address 9
[ 3299.942235] usb 2-4: configuration #1 chosen from 1 choice
[ 3299.949017] scsi12 : SCSI emulation for USB Mass Storage devices
[ 3299.949356] usb-storage: device found at 9
[ 3299.949358] usb-storage: waiting for device to settle before scanning
[ 3299.989022] Machine check events logged
[ 3304.953020] usb-storage: device scan complete
[ 3304.955347] scsi 12:0:0:0: CD-ROM            HSPA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 3304.961579] sr1: scsi-1 drive
[ 3304.961676] sr 12:0:0:0: Attached scsi CD-ROM sr1
[ 3304.961741] sr 12:0:0:0: Attached scsi generic sg2 type 5
[ 3306.005826] usb 2-4: USB disconnect, address 9
[ 3306.380026] usb 2-4: new high speed USB device using ehci_hcd and address 10
[ 3306.515141] usb 2-4: configuration #1 chosen from 1 choice
[ 3306.519774] option 2-4:1.0: GSM modem (1-port) converter detected
[ 3306.519834] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[ 3306.519889] option 2-4:1.1: GSM modem (1-port) converter detected
[ 3306.519932] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[ 3306.522858] scsi13 : SCSI emulation for USB Mass Storage devices
[ 3306.523122] option 2-4:1.3: GSM modem (1-port) converter detected
[ 3306.523182] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
[ 3306.525899] usb-storage: device found at 10
[ 3306.525902] usb-storage: waiting for device to settle before scanning
[ 3311.525885] usb-storage: device scan complete
[ 3311.528143] scsi 13:0:0:0: CD-ROM            HSPA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 3311.528632] scsi 13:0:0:1: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[ 3311.534486] sr1: scsi-1 drive
[ 3311.534625] sr 13:0:0:0: Attached scsi CD-ROM sr1
[ 3311.534709] sr 13:0:0:0: Attached scsi generic sg2 type 5
[ 3311.534878] sd 13:0:0:1: Attached scsi generic sg3 type 0
[ 3311.538983] sd 13:0:0:1: [sdb] Attached SCSI removable disk
[ 3324.418046] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.418053] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.418059] Info fld=0x0
[ 3324.418061] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.418068] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d a0 00 00 02 00
[ 3324.418080] end_request: I/O error, dev sr1, sector 1324672
[ 3324.418085] __ratelimit: 6 callbacks suppressed
[ 3324.418088] Buffer I/O error on device sr1, logical block 165584
[ 3324.419910] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.419912] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.419915] Info fld=0x0
[ 3324.419917] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.419920] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d a0 00 00 02 00
[ 3324.419926] end_request: I/O error, dev sr1, sector 1324672
[ 3324.419928] Buffer I/O error on device sr1, logical block 165584
[ 3324.422038] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.422041] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.422044] Info fld=0x0
[ 3324.422045] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.422049] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d be 00 00 02 00
[ 3324.422056] end_request: I/O error, dev sr1, sector 1324792
[ 3324.422058] Buffer I/O error on device sr1, logical block 165599
[ 3324.423914] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.423918] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.423923] Info fld=0x0
[ 3324.423925] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.423931] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d be 00 00 02 00
[ 3324.423943] end_request: I/O error, dev sr1, sector 1324792
[ 3324.423946] Buffer I/O error on device sr1, logical block 165599
[ 3324.429917] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.429923] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.429928] Info fld=0x0
[ 3324.429930] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.429936] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.429948] end_request: I/O error, dev sr1, sector 1324800
[ 3324.429951] Buffer I/O error on device sr1, logical block 165600
[ 3324.431915] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.431920] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.431925] Info fld=0x0
[ 3324.431927] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.431933] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.431944] end_request: I/O error, dev sr1, sector 1324800
[ 3324.431947] Buffer I/O error on device sr1, logical block 165600
[ 3324.433914] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.433917] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.433920] Info fld=0x0
[ 3324.433921] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.433925] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.433932] end_request: I/O error, dev sr1, sector 1324800
[ 3324.433934] Buffer I/O error on device sr1, logical block 165600
[ 3324.435916] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.435921] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.435926] Info fld=0x0
[ 3324.435928] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.435934] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.435945] end_request: I/O error, dev sr1, sector 1324800
[ 3324.435949] Buffer I/O error on device sr1, logical block 165600
[ 3324.438037] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.438040] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.438043] Info fld=0x0
[ 3324.438045] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.438055] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.438067] end_request: I/O error, dev sr1, sector 1324800
[ 3324.438070] Buffer I/O error on device sr1, logical block 165600
[ 3324.443045] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.443050] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.443055] Info fld=0x0
[ 3324.443057] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.443063] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.443074] end_request: I/O error, dev sr1, sector 1324800
[ 3324.443078] Buffer I/O error on device sr1, logical block 165600
[ 3324.444920] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.444923] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.444926] Info fld=0x0
[ 3324.444927] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.444931] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.444937] end_request: I/O error, dev sr1, sector 1324800
[ 3324.447036] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.447039] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.447042] Info fld=0x0
[ 3324.447044] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.447048] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d b2 00 00 02 00
[ 3324.447055] end_request: I/O error, dev sr1, sector 1324744
[ 3324.448915] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.448918] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.448921] Info fld=0x0
[ 3324.448923] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.448927] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d be 00 00 02 00
[ 3324.448934] end_request: I/O error, dev sr1, sector 1324792
[ 3324.451035] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.451038] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.451042] Info fld=0x0
[ 3324.451043] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.451047] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.451054] end_request: I/O error, dev sr1, sector 1324800
[ 3324.452915] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.452919] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.452922] Info fld=0x0
[ 3324.452923] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.452927] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.452935] end_request: I/O error, dev sr1, sector 1324800
[ 3324.455036] sr 13:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3324.455040] sr 13:0:0:0: [sr1] Sense Key : Illegal Request [current] 
[ 3324.455043] Info fld=0x0
[ 3324.455044] sr 13:0:0:0: [sr1] Add. Sense: Logical block address out of range
[ 3324.455048] sr 13:0:0:0: [sr1] CDB: Read(10): 28 00 00 05 0d c0 00 00 02 00
[ 3324.455056] end_request: I/O error, dev sr1, sector 1324800

---

### Post by taryneast on 2011-10-17
Well... no reply so far.

In the meantime, I've tried a few other things. 

This thread suggested using the command line to eject:
[http://ubuntuforums.org/showthread.php?t=1446727](http://ubuntuforums.org/showthread.php?t=1446727)

That did nothing until I removed the new stuff I put in udev. Now it does correctly eject the "scsi cd-rom" device... and stops all those annoying error messages... but still doesn't make the device appear.

I also noticed that lsusb seems to think my device is MF636 when it says MF112 on the back of it. I presume that's not good... but have no idea why it thinks that.


Anybody have any ideas?

---

### Post by pdc on 2011-10-18
so which version of ubuntu......

betavine has usb_modeswitch as part of the package; 

I used the eject command for an MF636 and did not need usb_modeswitch; 

......one can speculate about conflicting settings in your system now with various alterations.............. a clean install at some stage may clarify things.......... but I wouldn't rush into 11.10 ubuntu as there seem some reports of initial problems..............

---

### Post by taryneast on 2011-10-18
Version of ubuntu is Lucid


I've tried uninstalling usb_modeswitch.. makes no difference that I can see. It still loads as storage... I eject it, it sometimes reloads as a CD-ROM... then I eject it again.
...then big nothing happens.


I've tried ejecting by clicking the eject-icon from the file-list. 
I've tried "safely remove the drive". 
I've tried "eject cdrom5" from the command-line. 
I've tried clicking on the storage device to make sure it's mounted before doing all of the above.

Still nothing.

Clean install is sadly not an option for me. I need to work on this laptop and I have no other laptop/desktop to work on (I'm overseas for 4 more months).

I'd gladly go and look at settings, but which settings and where?
The device is simply not being even noticed as the modem that it is.... which is just plain weird. :(

---

### Post by taryneast on 2011-10-18
Oh, and I don't actually have an MF636. The device says MF112 on the back... but lsusb tells me it's loading as an MF636. this may well be part of the problem, but i don't know what's causing that.

any ideas?

---

### Post by taryneast on 2011-10-18
Ok... it's now showing up in the list of devices, so I thought I'd share what I did to get that working.

A friend f mine suggested reinstalling network-manager... which I was leery of doing in case it broke and I couldn't even connect by wifi (my last life-line).

But I went ahead and did it anyway - and for good measure checked if there were any "recommended packages" -> modemmanager was not installed but recommended, so I added that too.

No idea which one made it work, but now the device shows up in the list.

Currently still not actually connecting - but now it's there I can just play with config settings and I'm good.

---

### Post by taryneast on 2011-10-18
and the final touch was to delete the old "3 network" config settings and create a new one with the default connection settings.

All is good with the world once more.

---

### Post by pdc on 2011-10-18
well done; good work

we all learn from each other

---

