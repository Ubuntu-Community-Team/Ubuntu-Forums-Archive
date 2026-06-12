---
title: "Mount iPod touch"
date: 2012-08-16
forum: Multimedia Software
---

### Post by shayli147 on 2012-08-16
hello

sorry for the newbie question... my iPod touch seem to mount itself in an unreadable direction: afc://8058fb360cf5b9130497d1b6c37a1bc0306d19d8/

how can i mount it anyways?
where should i find the "iPod mount point" ?

i have searched in the internet about that AFC and how to change it's direction, tried to mount iPod mount point as Desktop (where it appears)and i have no clue for following steps...

i also followed this comment:
"" sebikul
February 18th, 2011, 02:17 AM

To fix tis issue you have to do the following:

1. Execute the following command:
$ ipod-read-sysinfo-extended

It should return :
"usage: ipod-read-sysinfo-extended <device|uuid|bus device> <mountpoint>"

If you get something telling to install a package, do it.

2. Execute the following command and copy the 40 character string:
$ lsusb -v | grep -i iSerial

3. Now execute this command to generate the hashinfo file:
$ ipod-read-sysinfo-extended <UUID> <mountpoint>

Being <UUID> the code you got in step 2 and mount point the absolute address of your iPod mountpoint, most likely being "/home/USER/.gvfs/NAME

Thats it, now it should work. ""

and the iSerial i copied is just like the directory...
 iSerial               3 8058fb360cf5b9130497d1b6c37a1bc0306d19d8
but yest didnt help, i got kinda lost in step 3, and i'm not even sure this could help me

thanks, Shay-li

---

### Post by nothingspecial on 2012-08-17
Question moved to it's own thread.

---

