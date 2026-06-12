---
title: "Preserve file timestamp: DLink 323 \ Ubuntu 9.04"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by blueberry7 on 2010-01-08
Hi,

I have a problem that I discovered whilst moving my digital photos to my newly acquired NAS, DLink DNS-323.

When I copied the files using Nautalus the timestamps changed to that of the date the copy took place. After a little Googling I found cp -p from the CLI should solve my problem. However this gave the error "cp: preserving times for `xxxx': Operation not permitted" where xxxx is the name of the file(s) I copied.

Being a persistent type I thought I'd try another way. Google revealed another "cure" for my problem could be to use "jhead" and have the affected files timestamps updated to that contained within the jpg meta-data. However using "jhead -ft" on my NAS mount-point gave a similar error "Error: Could not change time of file './test.jpg'".

I tried a few other commands; both chmod and chown on my NAS mount-point threw similar "Operation not permitted" errors.

I have tried using sudo in all cases as well.

This is my fstab entry for my NAS:-

```
//192.168.1.68/Volume_1/root /media/nas cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777    0    0
```The DNS-323 has no permissions set on it and files copied there are given the NAS default permissions:-

```
ls -l ./test.jpg 
-rwxrwxrwx 1 501 501 324538 2010-01-08 20:53 ./test.jpg
```I have a workaround; if I run "jhead -ft" from a Windows 2000 laptop against the NAS all file timestamps are corrected to that contained in the jpg's meta-data; as is the files' original timestamp preserved. Great.

The DNS-323 has 1.07 firmware and I believe Samba 3.x installed. I haven't been brave enough to put funbox on it so I can ssh in to it.

Can anybody provide any insight?

Thanks.

---

