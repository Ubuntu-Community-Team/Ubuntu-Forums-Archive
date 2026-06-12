---
title: "Unable to read DVD's and CD's and DVD drive"
date: 2013-11-17
forum: Multimedia Software
---

### Post by surrealillusions on 2013-11-17
Having some trouble getting DVD's and CD's to read.

I've recently gotten a new computer which is used for gaming, and my 2nd computer which runs Linux had a DVD drive which didn't work. I've swapped over the other DVD drive from the old computer into the Linux machine. This DVD drive worked under Windows 7 but doesn't work under Linux. Running Ubuntu 13.10.

Installed VLC player, tried both a DVD and an audio CD and nothing. I get this when trying to play them:

Playback failure:
DVDRead could not open the disc "/dev/dvd".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'cdda:///dev/cdrom'. Check the log for details.


I've tried to check the log, after finding out you needed to set it in the preferences, but nothing is saved to the log.

Saw about installing 'libdvdcss libdvdread4 libdvdnav4' via terminal, but, this is what I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libdvdcss' has no installation candidate



Then tried this:

sudo apt-get install regionset
Reading package lists... Done
Building dependency tree       
Reading state information... Done
regionset is already the newest version.
The following package was automatically installed and is no longer required:
  printer-driver-hpijs
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

followed by:

sudo regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.


Any suggestions?

---

### Post by oldos2er on 2013-11-17
DVDs are usually mounted to /dev/sr0; not sure about CDs.

---

### Post by surrealillusions on 2013-11-17
Ok, so how do I get the system to read that place for DVD's? Anyway to see if the drive is recognised by Ubuntu?

---

### Post by surrealillusions on 2013-11-17
Right..so, I've swapped the hard drive (with Linux on) and the DVD drive into the computer that the DVD drive initially was from. Works fine, I get a popup dialog asking what to do with a DVD. It plays fine, no stuttering, audio is fine etc...

What can be causing this DVD drive to not work in the other computer? Pretty sure I plugged it all in right. There's only 2 cables in the case that can reach the DVD drive.

Any ideas?

---

### Post by Yellow Pasque on 2013-11-17
Install lshw and give output of:
```
sudo lshw -sanitize -C disk
```

---

### Post by surrealillusions on 2013-11-18
*-disk                  
       description: ATA Disk
       product: WDC WD20EARS-00M
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 51.0
       serial: [REMOVED]
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=2bf73225-8503-472f-8b97-c5625fd3b68e sectorsize=512
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       configuration: sectorsize=512
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdc
       configuration: sectorsize=512
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sdd
       configuration: sectorsize=512
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sde
       configuration: sectorsize=512

---

### Post by Yellow Pasque on 2013-11-18
Well, it's not showing up in lshw. You should look through dmesg for clues:
```
dmesg
```

---

### Post by surrealillusions on 2013-11-18
> **Temüjin said:**
> Well, it's not showing up in lshw. You should look through dmesg for clues:
```
dmesg
```

Woah, thats alot of stuff when I do that...what do I need to look for in there?

---

### Post by Yellow Pasque on 2013-11-18
Pastebin it and I'll look through it: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by surrealillusions on 2013-11-18
Here we go: [http://paste.ubuntu.com/6439352/](http://paste.ubuntu.com/6439352/)

---

### Post by Yellow Pasque on 2013-11-18
Okay, no clues there. What kind of drive is this? SATA? PATA?

---

### Post by surrealillusions on 2013-11-18
I presume SATA, but not sure. How do I find out?

---

### Post by Yellow Pasque on 2013-11-18
Are you using a SATA cable or a PATA ribbon cable?

---

### Post by surrealillusions on 2013-11-18
Going off this image: [http://images.itreviews.com/www.itreviews.co.uk%2Fphotos%2Foptical_disk_connections.jpg](http://images.itreviews.com/www.itreviews.co.uk%2Fphotos%2Foptical_disk_connections.jpg)

Its a SATA.

---

### Post by Yellow Pasque on 2013-11-19
I'm a bit confused about what machine you currently have it in and what machine you're having a problem with.

So put the drive in the machine you're having an issue with and
1. Verify power and data cables are connected
2. Verify that the drive is seen in the BIOS. If it isn't, make sure you have it plugged in a working SATA port and/or try a different SATA data cable.

---

### Post by surrealillusions on 2013-11-19
> **Temüjin said:**
> I'm a bit confused about what machine you currently have it in and what machine you're having a problem with.

So put the drive in the machine you're having an issue with and
1. Verify power and data cables are connected
2. Verify that the drive is seen in the BIOS. If it isn't, make sure you have it plugged in a working SATA port and/or try a different SATA data cable.

Yep, drive in the machine. It has power as I can open/close it.

How do I know if its in bios? If it is, then how do I make it appear in Linux? If it isn't, then how do I get it recognised in bios?

Will see if I can use a different SATA cable but there's only 2 cables that can reach the DVD drive. Do these cables fail at all?

---

