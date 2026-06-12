---
title: "Media Tomb"
date: 2008-08-13
forum: Multimedia Software
---

### Post by thevoiceofalan on 2008-08-13
Hi All

I am currently experimenting with Media Tomb and have a problem adding media. 

If the Media is on the same harddisk as the OS then media tomb can browse to this with the filesystem view and add it to the video folder, but if I plug in an external hardrive (fat32) and try to browse using the filesystem to /media/MyBook for the external drive the cursor automatically jumbs back to /Media/ :(

I have a spare external drive that I think I will format to ext3 or similiar and have a go with

Any ideas? This is on ppc mac mini G4 with Ubuntu 8.*

---

### Post by vorgusa on 2008-08-13
hmm I am not sure about MediaTomb and fat32, but I have a seperate hard drive on my computer and it is able to access it just fine on ext3.  This might be a dumb question but can you access the files on the computer without using MediaTomb?

---

### Post by thevoiceofalan on 2008-08-13
yep access is no problem locally  :)

---

### Post by vorgusa on 2008-08-13
Were you able to give it a try with a ext3 Formatt?

---

### Post by thevoiceofalan on 2008-08-14
Didnt get a chance I will have a go this evening and post up..

---

### Post by thevoiceofalan on 2008-08-15
Yup looks like Media Tomb wont recognise a mounted fat 32 drive but the same drive as ext 2 no problemo :)

Cheers for the replys etc ;)

---

### Post by lindenRathen on 2009-01-07
I have a FAT32 formatted USB external hard drive and mediatomb did a similar thing for me (I would get the web interface click on /media/<ext HDD> and it would jump back to /media. 

BUT

I found that you can solve this by first running in a terminal:
```
sudo mediatomb
```

this then spewed a lot of set up read out to my screen the bottom of which was an IP address, copying this to firefox gave me access to the database screen but i could now access my external hard drive.

Hope this helps.

---

