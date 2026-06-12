---
title: "Windows XP cant access MY files"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by rynkrgr on 2011-05-08
Hi, I installed 11.04 about 2 days ago and only have limited experience with linux so forgive me for being a noob.

Im trying to recreate the network I had with my 2 family members computers before installing Ubuntu.  Ive installed samba and all that, and I can access the 2 windows XP computers shared files, but they cant access mine.

Heres some info:
The directory im trying to share is 
    /media/New Volume/SHARED

When I try to use the XP machine to access the ubuntu machine's shared file i get the error

\\RYANSERVER\SHARED is not accessible.  You might not have the permission to use this network resource.  
The network path was not found.

Any help would be awesome.[-o<

---

### Post by rynkrgr on 2011-05-08
Ok so I made a file at 

/home/ryan/share

and its sharing just fine.

For some reason its only giving me problems when I share a file thats in my second hard drive like 

/media/New Volume/trythis

---

### Post by ksprasad on 2011-05-08
Hi,
 
Maybe its because of the space between 'new' and 'volume'. Try renaming the drive without any space and check.
 
Regards,
ksprasad

---

### Post by rynkrgr on 2011-05-09
Sorry for the delay.

Ok, I renamed "New Volume" to "disk2" and made a new samba share folder on the second hard drive and still no luck.  Same errors as before. :(

---

### Post by rynkrgr on 2011-05-10
Bump.

If anyone has any suggestions Im willing to try them.

---

### Post by Morbius1 on 2011-05-10
How are you sharing the folder? The output of the following commands will tell us that:
```
net usershare info --long
testparm -s

```
The folder you are trying to share sure looks like an Windows filytype to me:
```
     /media/New Volume/SHARED
```
How are you mounting the partition /media/New Volume?

---

