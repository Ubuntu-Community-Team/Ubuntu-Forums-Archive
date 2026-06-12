---
title: "Accessing Samba Shares"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by PuK84 on 2010-01-08
Hi all,

Have an interesting problem. We have a linux server machine (9.10) and the way it is set up is various drives are mounted (to their own folder, of course) under one shared folder. Our Windoze PC's have no issue with accessing the shares, etc however when I mount the folder to my Ubuntu powered laptop all the folders are broken links. What have I done wrong?

---

### Post by Iowan on 2010-01-08
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To might help with some of the issues.

---

### Post by PuK84 on 2010-01-08
Maybe im missing something, but the problems listed in the how to didn't reflect the issue im having. Sorry, any other suggestions?

---

### Post by PuK84 on 2010-01-09
was speaking with my housemate and my laptop is seeing everything as symbollic links but we want my ubuntu to display them as folders. does that help at all?

---

### Post by PuK84 on 2010-01-16
Hi All,

I posted this in the general help section, but have now realised that this would be the best place for it.

Basically, we have a linux server (9.10) that has a bunch of hdd's mounted under one folder... if that makes sense... sounded better in my head, and that one main folder is shared. All our Windows PC's can access all the folders, etc without issue however my ubuntu laptop (9.10) keeps displaying all the folders as broken symbollic links. Any way to fix this? I would say it has something to do with my laptop as its the only one having issues.

---

### Post by Ilalmi on 2010-01-16
Hi,
have you tried other linux machines besides your laptop?
Could you give the output of ```
ls -la
``` in the folder into that the hdds are mounted?
Could you also give the output of ```
cat /etc/fstab
```?

---

### Post by Elfy on 2010-01-16
threads merged

---

### Post by PuK84 on 2010-01-17
Sorry, been away from home for the last couple of days. ok, here is the output of the two commands.

> $ ls -la
total 60
drwxr-xr-x 15 root   root   4096 2009-12-28 22:14 .
drwxr-xr-x 23 root   root   4096 2010-01-16 11:58 ..
drwxrwxrwx  2 root   root   4096 2009-12-28 22:08 Altruism
drwxrwxrwx  5 basket basket 4096 2009-12-29 09:10 Benevolance
drwxrwxrwx  2 root   root   4096 2009-12-28 22:09 BlackArmor
drwxrwxrwx  8 basket basket 4096 2010-01-09 17:26 Charity
drwxrwxrwx  2 root   root   4096 2009-12-28 22:08 Donation
drwxrwxrwx  7 basket basket 4096 2009-12-29 15:08 Generocity
drwxrwxrwx  2 root   root   4096 2009-12-28 22:08 Gifting
drwxrwxrwx  6 basket basket 4096 2009-12-29 11:37 Humanity
drwxrwxrwx  2 root   root   4096 2009-12-28 22:08 Koko1
drwxrwxrwx  2 root   root   4096 2009-12-28 22:08 Koko2
drwxrwxrwx  2 root   root   4096 2009-12-28 22:08 Koko3
drwxrwxrwx  5 basket basket 4096 2010-01-03 17:38 Philanthropy
drwxrwxrwx  8 basket basket 4096 2009-12-30 21:19 Sympathy


> $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sdb1 during installation ##################################################
UUID=282bf495-a5e2-4aaf-8f60-f38664f0591d /               ext4    errors=remount-ro 0       1

# swap was on /dev/sdb5 during installation ###############################################
UUID=b2670860-5fc8-47df-9826-f00b8f761b87 none            swap    sw              0       0

# CDROM ####################################################################################
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
############################################################################################

# /dev/sda1: LABEL="Gifting 400GB" UUID="5f4cf8b5-96b7-486e-b08a-b7ba7e4d5ae4" SEC_TYPE="ext2" TYPE="ext3"
#UUID=5f4cf8b5-96b7-486e-b08a-b7ba7e4d5ae4 /mnt/Gifting ext3 user,errors=remount-ro 0 2

# /dev/sdc1: LABEL="BlackArmor" UUID="3fc02937-333e-4008-ba79-739f7ac37aa1" TYPE="ext4"
#UUID=3fc02937-333e-4008-ba79-739f7ac37aa1 /mnt/BlackArmor ext4 user,errors=remount-ro 0 2

# /dev/sdd1: LABEL="Koko 2 500GB" UUID="43a62fad-e0ad-45bb-a3c6-0d187ddb1a32" TYPE="ext4"
#UUID=43a62fad-e0ad-45bb-a3c6-0d187ddb1a32 /mnt/Koko2 ext4 user,errors=remount-ro 0 2

# /dev/sde1: LABEL="Donation 640GB" UUID="c5399523-5d73-4c68-87cf-b379039e3f94" SEC_TYPE="ext2" TYPE="ext3"
#UUID=c5399523-5d73-4c68-87cf-b379039e3f94 /mnt/Donation ext3 user,errors=remount-ro 0 2

# /dev/sdf1: LABEL="Koko 3 500GB" UUID="3199a617-23b5-4cf8-9da0-720f424e859d" TYPE="ext4"
#UUID=3199a617-23b5-4cf8-9da0-720f424e859d /mnt/Koko3 ext4 user,errors=remount-ro 0 2

# /dev/sdh1: LABEL="Generocity 1TB" UUID="e3d961ea-3142-458e-acd8-53250ed536d0" TYPE="ext4"
UUID=e3d961ea-3142-458e-acd8-53250ed536d0 /mnt/Generocity ext4 user,errors=remount-ro 0 2

# /dev/sdg1: LABEL="Altruism 750GB" UUID="ec07656f-7112-40e1-ae9d-eacb1b8d564d" TYPE="ext4"
#UUID=ec07656f-7112-40e1-ae9d-eacb1b8d564d /mnt/Altruism ext4 user,errors=remount-ro 0 2

# /dev/sdi1: LABEL="Benelovance 1TB" UUID="8a669964-70c1-4405-9344-95b234033c12" TYPE="ext4"
UUID=8a669964-70c1-4405-9344-95b234033c12 /mnt/Benevolance ext4 user,errors=remount-ro 0 2

# /dev/sdn1: LABEL="Koko 1 320GB" UUID="dbd8c8aa-89d8-42db-b5ec-99d8a7c397f3" TYPE="ext4"
#UUID=dbd8c8aa-89d8-42db-b5ec-99d8a7c397f3 /mnt/Koko1 ext4 user,errors=remount-ro 0 2

# /dev/sdl1: LABEL="Charity 2TB" UUID="07eb8587-86b8-4ccf-aa5c-034df84c4bdd" TYPE="ext4"
UUID=07eb8587-86b8-4ccf-aa5c-034df84c4bdd /mnt/Charity ext4 user,errors=remount-ro 0 2

# /dev/sdm1: LABEL="Philanthropy 2TB" UUID="b9260517-bd47-4cdb-8d9c-df404fc37ab2" TYPE="ext4"
UUID=b9260517-bd47-4cdb-8d9c-df404fc37ab2 /mnt/Philanthropy ext4 user,errors=remount-ro 0 2

# /dev/sdj1: LABEL="Sympathy 1TB" UUID="d0d161d2-dc56-4c5d-a7d0-0e1cbcf95aa3" TYPE="ext4"
UUID=d0d161d2-dc56-4c5d-a7d0-0e1cbcf95aa3 /mnt/Sympathy ext4 user,errors=remount-ro 0 2

# /dev/sdk1: LABEL="Humanity 1TB" UUID="218fda6f-4d00-47a4-8239-5bb07eca2b7d" TYPE="ext4"
UUID=218fda6f-4d00-47a4-8239-5bb07eca2b7d /mnt/Humanity ext4 user,errors=remount-ro 0 2


---

### Post by Ilalmi on 2010-01-18
Darn! The output looks fine.

a) Can you access samba shares on a different server from your laptop?
b) Can you access the shares on your server from a different linux client?
c) What Ubuntu version runs on your laptop?
d) Try ```
unix extensions = no
``` in your samba server conf.

---

### Post by PuK84 on 2010-01-18
AH HAAAA!!! unix extensions made all well. why would this have fixed it though?

---

### Post by Ilalmi on 2010-01-22
Turning off unix extensions usually seems to help when dirs on a share can be accessed from windows clients while access from unix clients returns a broken link error.
It has something to do with sym- or hardlinks and/or user rights. 
I couldn't find a satisfying explanation for that behaviour.

---

