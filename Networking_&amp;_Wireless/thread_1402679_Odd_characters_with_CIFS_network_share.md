---
title: "Odd characters with CIFS network share"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by dbruns on 2010-02-09
I've got a few network shares on an EMC celerra SAN that I'm trying to mount on my ubuntu development server. 

Here are my fstab lines on my UBUNTU server:
//10.1.1.106/Artwork /mnt/artwork     smbfs   credentials=/root/.smbcredentials,dir_mode=0777,file_mode=0777,iocharset=utf8,mapchars    0 0
//10.1.1.106/WebFiles /mnt/webfiles     smbfs      defaults,username=user%PASSWORD,workgroup=company,file_mode=0777,dir_mode=0777,rw 0 0
This is what happens:
> $ sudo mount /mnt/webfiles/ && ls /mnt/webfiles
_~1  1.ai  C~1  ?Ma  r

$ sudo mount /mnt/artwork/ && ls /mnt/artwork
ã&#133;&#139;á&#152;&#152;í£ã&#147;&#147;  F~1  P  á&#147;£ä¾£ç&#158;&#148;æ&#151;¼  è&#130;æ¢®í&#134;&#132;?

On my SUSE production server this is what I have in my fstab:
> 
//10.1.1.106/WebFiles /mnt/webfiles     smbfs      defaults,username=user%Password,workgroup=company,dmask=777,fmask=777,rw 0 0

which results in:

> 
>ls /mnt/webfiles
logs  sales_attachments  tmp  WebBackup


I've tried different iocharsets, mapchars, leaving those options out and a number of other options, but the network shares I mount on my ubuntu server have all those weird characters.


Any help on this is much appreciated.

---

### Post by dmizer on 2010-02-09
Is the locale different on the Ubuntu development server and the SUSE production server?

---

### Post by dbruns on 2010-02-09
echo $LANG
en_US.UTF-8

for both

Also same for:
> $ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

---

### Post by dbruns on 2010-02-09
it may be worth noting that i'm using an older version of SLES that is still using smbfs, but that may not make a difference.

---

### Post by dbruns on 2010-02-09
Also, I've tried to mount the artwork directory from the SUSE box and everything worked fine. 

This is sooo frustrating.

---

### Post by dbruns on 2010-02-10
I created an NFS share and it seems to work just fine. It would be nice to get the CIFS shares working though.

---

