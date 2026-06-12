---
title: "mdadmin RAID5 very slow Write speed"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by jman177 on 2011-07-05
Hi 

I am hoping someone can help me I setup a brand new ubuntu 11.04 64bit system with:-

AMD Phoenom 840 (3.7GHz overclocked) 
8GB DDR3 RAM.
WD20EARS x 4
madmin (RAID5) Setup

For some reason I cannot get the write speed above 15mb/s & I have tried modifying the cache_Stripe_size from 256 to 8192.

My read speeds are great burst at 120mb/s & stable at about 60mb/s.

The only other possiblility is it could be my HDs which I read causes slow writes not sure if thats true though.

Please could someone point me in the right direction so I can fix this issue as I don't want to move to the dark side (Windows) .

---

### Post by jman177 on 2011-07-07
I found a solution to my 10mb/s write speed it now runs at 40mb/s wrtie speed. Please find below my fix:-

(Plase do this when you can have a 12-24 hours downtime)

Go to "Disk Uti" disconnect any partions & do a "Check Array"

Another thing I noticed when doing a copy from Win7 to Ubuntu SMB share which is larger than the available space it will slow down till you have filled the completely filled the disk

(eg. Had it start at 60mb/s & drop to 1mb/s and then Win7 gave me the no space message after about 10 minutes on a 2GB file)

If you change your cache from 256 to 8192 this will increase ytour write speed from 40mb/s to about 60mb/s or more.

---

