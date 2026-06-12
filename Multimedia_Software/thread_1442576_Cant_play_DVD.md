---
title: "Cant play DVD"
date: 2010-03-30
forum: Multimedia Software
---

### Post by shikhar_sharma on 2010-03-30
Hi guys,

I have a ubuntu 9.10 on my aspire one.previously i had windows and through it i burned a few dvd's with hidden files on it.Now i cant view it in ubuntu.CTRL+H shows me all the hidden files of the ubuntu system but it does not show me the files on the disc.When i tried running nautilus as a root then in the media folder it doesnt show the dvd as mounted.I really need these files.I know the files are in dvd as i can view it in my dad's XP laptop.
Any help would be appreciated

---

### Post by 0x656b694d on 2010-03-30
Hi,

What does [FONT="Courier New"]ls -la[/FONT] say on the DVD root directory?
What is the file system of the DVDs?

---

### Post by shikhar_sharma on 2010-03-30
ls -la gave me the following output :

root@shikhar-laptop:/media/cdrom0# ls -la
total 8
dr-xr-xr-x 2 4294967295 4294967295 2500 2009-12-27 23:27 .
drwxr-xr-x 3 root       root       4096 2010-03-30 03:23 ..

I dont know wat that means......

---

### Post by shikhar_sharma on 2010-03-30
One more info the filesystem is udf and when i click on properties on the DVD it says :

Contents : Nothing
0 bytes used
0 bytes free
Total capacity 0 bytes
Free space : Unknown

---

### Post by 0x656b694d on 2010-03-30
check what does [FONT="Courier New"]mount | grep cdrom[/FONT] say.

if it's empty, try this:
```

$ sudo umount /media/cdrom0
$ sudo mount /dev/scd0 /media/cdrom0/ -t udf

```

---

### Post by 0x656b694d on 2010-03-30
also check what's in the /etc/fstab:
```
$ grep cdrom /etc/fstab
```

i read ([http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/](http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/)) that it's recommended to have:
```
/dev/scd0 /media/cdrom0 **auto** user,noauto 0 0
```

unfortunately, i don't have a UDF DVD to check.

---

### Post by shikhar_sharma on 2010-04-04
Hey thanks for the reply man.i tried ur suggestion too but it still doesnt work.see my problem is not with mounting of udf file system because i can get every other damm dvd to work but its just that these dvd's with hidden files on it are not being displayed.These are perfect in windows but in ubuntu i dont know why they are not visible.

---

