---
title: "Vobcopy does not ripp the whole dvd (only first chapter)..."
date: 2009-06-14
forum: Multimedia Software
---

### Post by killabee44 on 2009-06-14
Guys,

I have Vobcopy installed on my Kubuntu pc and it works, except for the fact that it only ripps the first chapter of the dvd. 

I can browse all the chapters from Dolphin but every time I try to ripp this DVD it only does the first chapter. Is there a way to get it to see all of them? 

I did not see any option for that when I did a  ```
vobcopy -h
```

I am using version 1.1.0. Am I missing something?

This is the command I am running:

```
vobcopy -i /dev/scd0 -o ~/DVDs/ -l
```

This all is on a Kubuntu Jaunty machine. Thanks.

---

### Post by killabee44 on 2009-06-14
Option -m gave me a mirror copy of the dvd, so I guess that will work.

---

### Post by killabee44 on 2009-06-14
HMM, Looks like my problem might be the way my fstab is set up. It says CD Rom, but not DVD. When I use the 

vobcopy -i /dev/scd0 -o ~/DVDs/ -l

It will only copy the first chapter because it thinks that the DVD is really a CD Rom. The question is, how can I change my Fstab file so that the system knows that I have two dvd drives installed and not Cdrom's?

Can I simply change the text "CDRom" to DVD? 



My Fstab looks like:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

Thanks for any help..

---

### Post by mc4man on 2009-06-14
there's nothing wrong with your fstab
For vobcopy use the -m to mirror the whole disk or -n for the title only (where n is the title number

By default vobcopy assumes the disk is in /media/cdrom0 and doesn't need a path specified. Otherwise you need to use -i /path/to/mounted/dvd 
For example  -i /media/cdrom1

My default command is 
vobcopy -v -m -F 16 

Though actually because I have 2 drives vobcopy launches from a script that's been made an auto run choice

```
#!/bin/bash
gnome-terminal -e "vobcopy -v -m -F 16" /media/*
```


Edit:
It's better if you use -i to specify the mount point, not the device. So as noted if it's /media/cdrom0 than no need to use -i, if it's media/cdrom1 than use the -i

You only need the -l if your ripping a title only (-n) To one large .VOB

Ex. based on your last comm. does the whole disk (-m) from your /dev/scd0 drive

```
vobcopy -m -o ~/DVDs/
```

---

### Post by killabee44 on 2009-06-15
Mc4man,

Thanks for your help. I was finally able to get it working but found something interesting. When I do a: 

```
vobcopy -m -o ~/DVDs/
```

Vobcopy will only write the first chapter of the DVD to the directory specified and ignore the -m command (mirror). I ended up having to put the -m switch at the end of the complete command in order to get it to work properly. I had to do it this way:

```
vobcopy -o ~/DVDs/ -m
```

That worked as expected. Thanks again.


Killabee44

---

### Post by mc4man on 2009-06-15
That is odd that the placement of -m mattered, doesn't on 8.04, 8.10 (ubuntu

Maybe a 9.04 or 9.04 kubuntu thing, though whatever works is obviously the best way.

(if you run into structured protected titles drop me a line, there are some workarounds - (you'll start seeing a  lot of 'had to skip's

---

