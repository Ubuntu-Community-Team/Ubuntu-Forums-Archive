---
title: "file sharing error i've never seen"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by learning_ on 2011-01-04
I have encountered many problems in Ubuntu, many of which I have been able to figure out how to fix myself (except a few tricky ones). 

Found a new one recently that I just cannot figure out. I have set up file sharing on my network between two systems running Ubuntu 10.04 (Lucid Lynx), one a desktop and the other a laptop. I Installed the proper packages on both systems, and it seemed to be working properly. However, on the laptop, when I try to mount or access the public-files of the desktop or laptop I receive the following error:


```
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```


I have been struggling with this for hours, tirelessly googling to no avail.](*,)
I did find one thing that works, clicking frantically like a mad man as the error windows pile up until the password prompt appears, but I feel that may be an impractical approach. 

Any and all help is appreciated in advance.

---

### Post by drpjkurian on 2011-01-04
Try this
I found this in another post written by jimi_bond
I found a workaround by setting up a directory in my media directory

mkdir /media/stuart_02

then adding this line to the bottom of my /etc/fstab file

//[IP_ADDRESS_OF_SHARE]/[SHARE_NAME] /media/stuart_02 smbfs rw,auto,user=[USERNAME],password=[PASSWORD]	0 0

thats the user name and password of the PC were the folder is you wish to mount, in my case the windows PC.

you can then either reboot or run this command

sudo mount -a

and you should see an icon appear on your desktop.

---

### Post by drpjkurian on 2011-01-04
Try this
I found this in another post written by jimi_bond
I found a workaround by setting up a directory in my media directory

mkdir /media/stuart_02

then adding this line to the bottom of my /etc/fstab file

//[IP_ADDRESS_OF_SHARE]/[SHARE_NAME] /media/stuart_02 smbfs rw,auto,user=[USERNAME],password=[PASSWORD]	0 0

thats the user name and password of the PC were the folder is you wish to mount, in my case the windows PC.

you can then either reboot or run this command

sudo mount -a

and you should see an icon appear on your desktop.

---

### Post by learning_ on 2011-01-05
would I just copy and paste that right in (with the proper names and such) straight to the file or is it supposed to be lined up a certain way? I'm very nervous when it comes to editing these files...:confused:

---

### Post by PatchesTheCaveman on 2011-01-05
It will work as provided, since a space is all that's necessary to separate each option.  However, you can add all the TABs you want to make it line up and look pretty if you want.  It will work either way.

---

