---
title: "Got the samba cifs share working in mythtv!"
date: 2014-02-27
forum: Mythbuntu
---

### Post by sdowney717 on 2014-02-27
You have to enter your mount command in /etc/fstab
after you edit fstab you test by typing 'sudo mount -a' in the terminal window.

When you have a space in your shared windows folder, you must put \040 in its place
my share is not password protected, so guest works.
this line works for me in fstab

> //192.168.1.7/users/public/Recorded\040Tv /mnt cifs guest,uid=1000,iocharset=utf8 0 0


space mention here -- [http://ironman.darthgibus.net/?p=136](http://ironman.darthgibus.net/?p=136)

fstab help here -- [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

In mythbackend, this has to go in videos your mounted folder name.
I have 2 folders setup, one to the share at /mnt
the other to my second drive at /media/scott/05fruiyr98789u4

Hit m then scan for change and all the video files then appear in the video tab of myth front end.

---

