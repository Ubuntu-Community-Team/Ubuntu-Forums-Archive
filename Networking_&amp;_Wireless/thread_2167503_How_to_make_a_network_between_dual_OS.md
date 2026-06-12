---
title: "How to make a network between dual OS"
date: 2013-08-13
forum: Networking &amp; Wireless
---

### Post by nachinew on 2013-08-13
Hi,

How to make a network sharing between two OS installed in a same HDD?

I am using Ubuntu and Win 8, While I am using Win 8 I need to use some common entertainment files or documents from Ubuntu and Vice versa.

It is possible? Possible means what is the procedure and Guides.

---

### Post by newbie-user on 2013-08-13
Yeah, it can be done. Just create a separate partition on the hard drive and format it as FAT32. Then put whatever files you want to transfer into that partition. Both Ubuntu and Win8 will be able to read from it.

---

### Post by nachinew on 2013-08-14
> **newbie-user said:**
> Yeah, it can be done. Just create a separate partition on the hard drive and format it as FAT32. Then put whatever files you want to transfer into that partition. Both Ubuntu and Win8 will be able to read from it.

Thanks for your help, I will try and let you know if any issue I found.

---

### Post by QIII on 2013-08-14
I would make that partition NTFS.  FAT32 has file size and other limitations that might prove troublesome.

---

### Post by Skateinmars on 2013-08-14
I second the NTFS choice.
Using a somewhat recent version of Ubuntu there shouldn't be any problem with it.

---

