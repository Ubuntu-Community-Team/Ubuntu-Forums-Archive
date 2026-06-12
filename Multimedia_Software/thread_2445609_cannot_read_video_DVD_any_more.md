---
title: "cannot read video DVD any more"
date: 2020-06-17
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2020-06-17
Hi, I have an old Dell Latitude E5510 laptop which I have not used for a while. A friend wants a laptop and it has a respectable 8 G of ram so I am fixing it up for him. The laptop is old, it has a dvd drive. I thought it would be a bonus since new laptops don't come with dvd drives anymore. It works for audio CDs but it doesn't recognize video DVDs. Pop in a DVD video it doesn't do anything. Tried to manually open the media with vlc it just quit with error (but no description of error) Regionset complains that there is no disc in the drive. Tried a few dvds with same result.

I have installed libdvdcss2, libdvdread and libdvdnav already. 

The Video DVDs I am using for test now used to work when I was using this laptop some years ago (with Ubuntu 14.04?) I had ripped them with handbrake on this machine.

```
 sudo lshw -C disk
[sudo] password for testaccount: 
  *-disk                    
       description: ATA Disk
       product: WDC WD2500BEKT-7
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1A01
       serial: WD-WXE1A70R6788
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=75059ed8
  *-cdrom
       description: DVD reader
       product: DVD-ROM DV-28SW
       vendor: TEAC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/sr0
       version: 3.2B
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc

```


Kubuntu 20.04.

---

### Post by CelticWarrior on 2020-06-17
CDs and DVDs are read by different lasers. It often happens in old drives that only one fails.

---

