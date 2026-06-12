---
title: "cannot see DVD drive in ubuntu 11.10"
date: 2011-10-22
forum: Multimedia Software
---

### Post by kommissario on 2011-10-22
Hello All,

I built a desktop PC myself and I decided to install Ubuntu 11.10 (64 bit) on it. All went ok but I have an issue with the DVD drive. I do not see it. 

I searched on the web for similar issues and I tried: 

```
sudo  wodim --devices 

```

wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg2'	rwrw-- : 'hp' 'BD-RE  BH20L'
-------------------------------------------------------------------------


that's actually my DVD drive ... so I tried


```
sudo  mkdir /media/cdrom 
```

```
sudo  mount -t iso9660 /dev/sg2 /media/cdrom
```

... but I got: 

 sudo  mount -t iso9660 /dev/sg2 /media/cdrom
mount: /dev/sg2 is not a block device



Can someone help me out?

Thanks!;)

---

### Post by mc4man on 2011-10-23
Why don't you post what's shown here 
```
sudo lshw -C disk
```

---

### Post by kommissario on 2011-10-23
*-cdrom                 
       description: DVD-RAM writer
       product: BD-RE  BH20L
       vendor: hp
       physical id: 0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: B577
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: OCZ-AGILITY3
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 2.11
       serial: OCZ-27P7U4JYIO16O28U
       size: 55GiB (60GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000594d3

---

### Post by JD8182 on 2011-10-23
Is there a Disc in the DVD writer currently? Sometimes the icon does not show up unless there is a disc in the player? Just a thought...



> **kommissario said:**
> Hello All,

I built a desktop PC myself and I decided to install Ubuntu 11.10 (64 bit) on it. All went ok but I have an issue with the DVD drive. I do not see it. 

I searched on the web for similar issues and I tried: 

```
sudo  wodim --devices 

```

wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg2'	rwrw-- : 'hp' 'BD-RE  BH20L'
-------------------------------------------------------------------------


that's actually my DVD drive ... so I tried


```
sudo  mkdir /media/cdrom 
```

```
sudo  mount -t iso9660 /dev/sg2 /media/cdrom
```

... but I got: 

 sudo  mount -t iso9660 /dev/sg2 /media/cdrom
mount: /dev/sg2 is not a block device



Can someone help me out?

Thanks!;)

---

### Post by kommissario on 2011-10-23
yes, there is an original DVD (movie) on it

---

### Post by kommissario on 2011-10-23
just installed a VM (virtualbox) using this dvd drive with no issue ... any idea why can't see it in the OS?

---

### Post by kommissario on 2011-10-23
my bad here ...

when I finished the installation of Windows in Virtual BOX I could see the icon in the desktop with the DVD-R on it ... 

This means that the issue is not with the Drive, but with the original movies ... I can't play only them, I followed the procedure for the extras and unrestricted, but probably there is more I have to do for it.

I will mark this as solved and I will search for a solution. Thanks to all who helped me.

---

