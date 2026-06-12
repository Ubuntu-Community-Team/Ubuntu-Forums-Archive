---
title: "Trying to access pictures, very new too linux!"
date: 2008-06-16
forum: Multimedia Software
---

### Post by Latak on 2008-06-16
I am running xubuntu and i log in using xfce. I have a dvd with pitures on it and when i try too access it i get "access denied". i have tryed typin sudo -s then password to get in root, but like i said i am extremely new to linux and could use a hand :-p

---

### Post by Latak on 2008-06-17
/bump

---

### Post by nunki on 2008-06-17
When you put the disk in the drive does it get mounted? Does an icon appear on your desktop?

Also, post the output of 
```

cat /etc/fstab

```

---

### Post by Latak on 2008-06-17
alex@alex:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7d456b89-4455-425d-9a1b-06da0dcf7a66 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1c8cd61d-21e5-4dc9-988f-2a7de5dd26e9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



And yes it does mount, i can click the icon and see all the files but i just cant open them

---

### Post by nunki on 2008-06-17
Interesting. Try 
```

cd /media/cdrom0

```
and post relevant output of 
```

ls -lrt

```

---

### Post by Latak on 2008-06-17
Ok 

alex@alex:~$ cd /media/cdrom0
alex@alex:/media/cdrom0$ ls -lrt
total 130419
-rw------- 1 501 501 1548823 2005-12-23 22:15 alex-dman-benny.jpg
-rw------- 1 501 501 2954734 2006-04-20 23:39 skate-alex-3flip.jpg




i only posted the first two files, im not sure if its relevant at all though. lol

---

### Post by nunki on 2008-06-17
Ok post the output of 
```

id alex

```

Im sure it will be 501, but just making sure. Im wondering if you dont have permissions to use the image viewer program, and thats whats giving you the error. Have you viewed images from the cdrom before? What program do you use? I think GQview is the xubuntu viewer, but Im not sure. Try
```

gqview 

```
and point it at one of the files on your dvd

---

### Post by Latak on 2008-06-17
alex@alex:/media/cdrom0$ id alex
uid=1000(alex) gid=1000(alex) groups=1000(alex),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin)



nope i have not looked at files from my cdrom before, this is a brand new computer. and i believe Image viewer is the program that i am trying to use

this is such a stupid problem to have lol :-(

---

### Post by Latak on 2008-06-18
bump

---

