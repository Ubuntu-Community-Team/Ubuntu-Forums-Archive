---
title: "Vobcopy question"
date: 2008-08-16
forum: Multimedia Software
---

### Post by klemperal on 2008-08-16
Hi folks,

Anyone here familiar with Vobcopy? I'm trying to figure out how I can get it to rip the dvd to a specific folder within my home folder rather then directly to my home folder. For example, I want the ripped DVD in /home/rick/dvdrips and not the default /home/rick.

thanks

---

### Post by mc4man on 2008-08-16
Use an -o option
ex.
 vobcopy -v -m -o /home/rick/dvdrips -F 16 

will rip in verbose mode (-v), mirroring the whole disk (-m), to dvdrips with a readahead of 16 sectors (-F 16)

if the disk is not mounted to default /media/cdrom0 then add path at end
ex.
 vobcopy -v -m -o /home/rick/dvdrips -F 16 /media/cdrom1

Edit: was that you over at doom9? (DvdRb in wine)

---

