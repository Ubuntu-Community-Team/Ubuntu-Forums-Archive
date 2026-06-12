---
title: "Can't burn DVDs"
date: 2009-01-03
forum: Multimedia Software
---

### Post by salazarah on 2009-01-03
Hi everybody.

I have a problem with my dvd writer, when I try to burn a dvd (both: -R and +R) with brasero I says that the disk has 0 free bytes, but is a new one (I tried several disks with the same result). Here is the result of lshw:

 *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GH22NP20
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open

Basically i can't write dvd, but have no problem with cd, I can write them normally. Also i am using 8.04.
If somebody can help me I will appreciate it.

---

### Post by namdung on 2009-01-03
The Brasero in Ubuntu Repository may be old.
[http://projects.gnome.org/brasero/](http://projects.gnome.org/brasero/)

Try K3b to burn a DVD and see if works. If it does then issue with Brasero. If it doesn't then issue with ur hardware, disk or some other general issue.

---

### Post by salazarah on 2009-01-04
Namdung, I already tried to burn disks with k3b even with nerolinux with the same results. I will try with another dvd drive.

Thanks for the advise

---

### Post by airbornemist6 on 2009-01-11
I have the same problem.

EDIT:
The default Ubuntu CD/DVD writer works, it's just Brasero that doesn't...

---

### Post by GCCC on 2009-02-03
> **airbornemist6 said:**
> I have the same problem.

EDIT:
The default Ubuntu CD/DVD writer works, it's just Brasero that doesn't...

Thank you for making this edit.  I have an LG GH22NP20 in an external enclosure and was having the same problem also.  Using the default writer worked for me as well.

---

