---
title: "cant add rw permissions to fat partition using pysdm"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by eduardoavdr on 2010-06-20
Hi all,

Im trying to share a fat partition using samba. The sharing thing is not a problem thanks to samba which works perfectly.

The problem is with the partition Im willing to share over my network. Everytime I reboot my machine, I have to go to Places and select the Fat drive.

I have read that I have to modify the fstab file to make it automontable. For this I have used pysdm to admin the fat partition and make it automontable. It works fine but Im unable to give write permisions to everyone to write over this drive. Even my user when using ubuntu has no write permisions on this drive.

These are the comand Im using for pysdm 

$sudo pysdm

And these are the params Im setting in fstab file with pysdm:

/dev/sdb1  /media/sdb1  vfat  umask=777,dmask=777,fmask=777  0  0

Ubuntu wont mount the drive with this settings, only with "defaults"

Thanks for your help!

---

### Post by Morbius1 on 2010-06-20
umask=777 will turn off read, write , and everything else off. The more traditional way of doing this is this:

```
/dev/sdb1 /media/sdb1 vfat utf8,umask=000 0 0
```

---

### Post by eduardoavdr on 2010-06-21
Thank you very very much Morbius1! That worked without any problems!
Excellent! :guitar:

cheers!

---

