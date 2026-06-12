---
title: "DVD Burner Install/Setup"
date: 2008-06-04
forum: Mythbuntu
---

### Post by Deathrend on 2008-06-04
I recently bought a new DVD burner for my MythTV box, however I'm not exactly sure what I'm doing.  I'm fairly new to Linux so bare with me here..

I'm guessing it would need to be listed in Fstab, currently listed is:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

That is my DVD-Rom (Which is still in the box).

"lshw" output shows:

```

           *-cdrom:0
                description: DVD-RAM writer
                product: DVD A  DH20A4P
                vendor: ATAPI
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 9P59
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
           *-cdrom:1
                description: DVD reader
                product: DVD SOHD-16P9S
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: FQSD
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open


```

The DVD Burner I added is the master, DVD-Rom slave. What should I do from here, add "/dev/scd1" to the fstab for the DVD-rom, anything need to change for the old line (seeing as the drive changed in that position)?

Once this is setup, what needs to be changed inside Mythbuntu as well, to allow burning of DVD's?

---

