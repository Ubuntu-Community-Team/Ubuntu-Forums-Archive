---
title: "External DVD/CD does not recognize audio CDs"
date: 2015-05-23
forum: Multimedia Software
---

### Post by Polar Humenn on 2015-05-23
Greetings,

I have a Memorex 32023288 DVD/CD 16x external connected via USB. It will mount and explore any ISO, but it will not recognize any CD-audio disk, mp3s or older standard CD-audios. Is there anything I must do, like install a special library or something? Note, I can mount things like Linux disks, FAT disks with Joliet Extensions, etc. but CD-audio seems to be not working. 

Any insights?

Below is the "lsusb" for that device and some of the syslog for the device with a CD-audio disk inside.


```
# lsusb 
Bus 003 Device 008: ID 4855:3288 Memorex 

# tail -f /var/log/syslog
May 23 13:25:34 adiron kernel: [610919.584906] usb 3-6: new high-speed USB device number 7 using xhci_hcd
May 23 13:25:34 adiron kernel: [610919.602148] usb 3-6: New USB device found, idVendor=4855, idProduct=3288
May 23 13:25:34 adiron kernel: [610919.602155] usb 3-6: New USB device strings: Mfr=56, Product=64, SerialNumber=83
May 23 13:25:34 adiron kernel: [610919.602159] usb 3-6: Product: 1394/USB 2.0 Drive
May 23 13:25:34 adiron kernel: [610919.602162] usb 3-6: Manufacturer: Memorex
May 23 13:25:34 adiron kernel: [610919.602165] usb 3-6: SerialNumber: 0617015347
May 23 13:25:34 adiron kernel: [610919.602875] usb-storage 3-6:1.0: USB Mass Storage device detected
May 23 13:25:34 adiron kernel: [610919.603025] scsi7 : usb-storage 3-6:1.0
May 23 13:25:34 adiron mtp-probe: checking bus 3, device 7: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6"
May 23 13:25:34 adiron mtp-probe: bus: 3, device: 7 was not an MTP device
May 23 13:25:35 adiron kernel: [610920.601060] scsi 7:0:0:0: CD-ROM            Memorex  DVD+-RAM 510L v1 MWS7 PQ: 0 ANSI: 0
May 23 13:25:35 adiron kernel: [610920.603780] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May 23 13:25:35 adiron kernel: [610920.603782] cdrom: Uniform CD-ROM driver Revision: 3.20
May 23 13:25:35 adiron kernel: [610920.603900] sr 7:0:0:0: Attached scsi CD-ROM sr0
May 23 13:25:35 adiron kernel: [610920.604957] sr 7:0:0:0: Attached scsi generic sg4 type 5
May 23 13:30:36 adiron kernel: [611220.696176] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 6 ep 16 with no TDs queued?
May 23 13:30:36 adiron kernel: [611220.696775] sr 7:0:0:0: [sr0]
May 23 13:30:36 adiron kernel: [611220.696777] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 23 13:30:36 adiron kernel: [611220.696778] sr 7:0:0:0: [sr0]
May 23 13:30:36 adiron kernel: [611220.696779] Sense Key : Illegal Request [current]
May 23 13:30:36 adiron kernel: [611220.696781] sr 7:0:0:0: [sr0]
May 23 13:30:36 adiron kernel: [611220.696783] Add. Sense: Illegal mode for this track
May 23 13:30:36 adiron kernel: [611220.696784] sr 7:0:0:0: [sr0] CDB:
May 23 13:30:36 adiron kernel: [611220.696784] Read(10): 28 00 00 00 00 00 00 00 08 00
May 23 13:30:36 adiron kernel: [6 11220.696788] end_request: I/O error, dev sr0, sector 0
May 23 13:30:36 adiron kernel: [611220.696790] Buffer I/O error on device sr0, logical block 0
May 23 13:30:36 adiron kernel: [611220.696791] Buffer I/O error on device sr0, logical block 1
May 23 13:30:36 adiron kernel: [611220.696793] Buffer I/O error on device sr0, logical block 2
May 23 13:30:36 adiron kernel: [611220.696794] Buffer I/O error on device sr0, logical block 3
May 23 13:30:36 adiron kernel: [611220.696795] Buffer I/O error on device sr0, logical block 4
May 23 13:30:36 adiron kernel: [611220.696796] Buffer I/O error on device sr0, logical block 5
May 23 13:30:36 adiron kernel: [611220.696796] Buffer I/O error on device sr0, logical block 6
May 23 13:30:36 adiron kernel: [611220.696797] Buffer I/O error on device sr0, logical block 7
May 23 13:30:36 adiron kernel: [611220.697988] sr 7:0:0:0: [sr0] 
May 23 13:30:36 adiron kernel: [611220.697989] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 23 13:30:36 adiron kernel: [611220.697990] sr 7:0:0:0: [sr0] 
May 23 13:30:36 adiron kernel: [611220.697991] Sense Key : Illegal Request [current]
May 23 13:30:36 adiron kernel: [611220.697992] sr 7:0:0:0: [sr0] 
May 23 13:30:36 adiron kernel: [611220.697993] Add. Sense: Illegal mode for this track
May 23 13:30:36 adiron kernel: [611220.697994] sr 7:0:0:0: [sr0] CDB:
May 23 13:30:36 adiron kernel: [611220.697994] Read(10): 28 00 00 00 00 00 00 00 01 00
May 23 13:30:36 adiron kernel: [611220.697997] end_request: I/O error, dev sr0, sector 0
May 23 13:30:36 adiron kernel: [611220.697998] Buffer I/O error on device sr0, logical block 0
May 23 13:30:36 adiron kernel: [611220.699231] sr 7:0:0:0: [sr0] 
May 23 13:30:36 adiron kernel: [611220.699233] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 23 13:30:36 adiron kernel: [611220.699234] sr 7:0:0:0: [sr0] 
May 23 13:30:36 adiron kernel: [611220.699235] Sense Key : Illegal Request [current]
May 23 13:30:36 adiron kernel: [611220.699237] sr 7:0:0:0: [sr0] 
May 23 13:30:36 adiron kernel: [611220.699238] Add. Sense: Illegal mode for this track
May 23 13:30:36 adiron kernel: [611220.699239] sr 7:0:0:0: [sr0] CDB:
May 23 13:30:36 adiron kernel: [611220.699240] Read(10): 28 00 00 00 00 01 00 00 01 00

```

---

