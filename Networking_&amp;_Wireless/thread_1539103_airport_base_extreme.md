---
title: "airport base extreme"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by bcampbe81 on 2010-07-26
Hi all so this is kind of a question and a how to get to where i'm at

I have 3 pc's at home which are the following

1x XP box
1x Ubuntu 10LTS dual boot vista (i know its bad)
1x Macbook Pro 

i also have an Airport Extreme Base station with a 1tb HD (formatted HFS+) in the AEBS as well as a printer

The HFS+ i would like to keep as HFS+ due to ease of use and file size (the drive has 4gig+ files so FAT32 was out and Airport doesnt support NTFS reading from OSX. I did try it... 2 days worth ... not worth it in the end.

My problem is that I would like the 1tb drive to mount automatically on boot in Ubuntu but currently doesnt work, 

I've installed hfsprogs installed and mounting manually with read write works with no problems and transfer speeds are not too different from direct connection to usb (about 10mb/s less but i can live with that)

i've added the following to /etc/fstab
```

//ipadressofABES/media    /media/Media cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

which i got from somewhere on this site, i've added the nounix and tried the domain=enterdomainhere options with nil success

its not much of a problem really as I can navigate to the drive through the gui with no issues. reading and writing is fine just wish i didnt have to mount it everytime as i would like it to just mount 

any help would be greatly appreciated

Thanks

B

---

### Post by bcampbe81 on 2010-07-26
Got it sorted

did 2 things

1) changed the password to the AEBS from "With a disk password" to "With AirPort Extreme password"

2) did the whole credentials file thingo and added the password only to the smb credentials file and edited fstab file as necessary (so new fstab entry is 

```

//ipaddressofAEBS/media    /media/Media        cifs    credentials=/home/myhomefolder/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

did a 
```

sudo mount -a

```

and BAM the problems gone

---

