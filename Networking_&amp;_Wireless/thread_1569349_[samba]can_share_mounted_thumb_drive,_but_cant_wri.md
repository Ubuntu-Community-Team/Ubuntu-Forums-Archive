---
title: "[samba]can share mounted thumb drive, but cant write"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by coldchillen on 2010-09-06
so after searching and reading, and searching some more, im stuck. i cant seem to get a mounted thumb drive to give write access. first thing to know is that, im using a seagate dockstar with a primary thumb drive[sda1] booting debian and samba. secondly, im a total newbie when it comes to linux. im pretty much learning as i go lol.

i guess you could say im still in the testing phase, just trying to make sure files can be shared, mounted and accessed by users. the problem is stated as the title. i have successfully shared a folder in sda1 with rw access, but i cant do the same for the second drive[sdb1].

for sda1 with rw access, here are the smb.conf settings:
```
[shared]

path = share
available = yes
valid users = mark
read only = no
browsable = yes
public = yes
writable = yes
```/share is owned by mark:mark

sdb1 is almost identical, except the path = share/USB2
however, /USB2 is owned by root:root; cant seem to change this. could this be the problem?

sdb1 fstab:
```
/dev/sdb1 /share/USB2 vfat rw,user,auto 0 0
```mtab:
```
/dev/sdb1 /share/USB2 vfat rw,nosuid,nodev,noexec,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro 0 0
```im not really sure what to do. ive tried adding: 
create mask = 777
directory mask = 777

any help would be appreciated, thanks!

---

### Post by coldchillen on 2010-09-07
ok, an update.

i switched an external hdd in place of the second usb stck, but the hdd is still identified as sdb1. the hdd mounts and its visible in other machines. i just cant get it to share or access directories and files within the hdd. any ideas?

---

