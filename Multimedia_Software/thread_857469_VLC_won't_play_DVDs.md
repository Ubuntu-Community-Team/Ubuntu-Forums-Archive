---
title: "VLC won't play DVDs"
date: 2008-07-12
forum: Multimedia Software
---

### Post by Jordanwb on 2008-07-12
I load VLC goto File->Open Disk. I put "/dev/dvd" into the "Device Name" box. I click OK. It recognizes the disk because in the status bar it says "MASHRY01" and the DVD spins up. But I don't get the menu. This happened before in Ubuntu, and Xubuntu as well as KDE on Arch and Debian and on more than one computer.

[Edit]

I run vlc from the terminal and I get this output:

> 
jordanwb@JORDAN-EE97700D:~$ sudo vlc
VLC media player 0.8.6e Janus
starting VLC root wrapper... using UID 1000 (jordanwb)
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: MASHYR01
libdvdnav: DVD Serial Number: 2B4B5DD5
libdvdnav: DVD Title (Alternative): MASHYR01
libdvdnav: Unable to find map file '/home/jordanwb/.dvdnav/MASHYR01.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[00000283] main playlist: nothing to play


---

### Post by mc4man on 2008-07-12
> sudo vlc No need to open vlc as root, just use vlc
> libdvdread: Encrypted DVD support unavailable. You need to install libdvdcss2
If you have medibuntu enabled as a third party source then just run 
```
sudo apt-get install libdvdcss2
```
If not go here and add repo as instructed for whatever ver. your using (hardy, gutsy, ect.) and then add libdvdcss2
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Elephantman5 on 2008-08-31
> **mc4man said:**
> No need to open vlc as root, just use vlc
 You need to install libdvdcss2
If you have medibuntu enabled as a third party source then just run 
```
sudo apt-get install libdvdcss2
```If not go here and add repo as instructed for whatever ver. your using (hardy, gutsy, ect.) and then add libdvdcss2
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

ajzimmerman@ajzimmerman-desktop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
ajzimmerman@ajzimmerman-desktop:~$

---

### Post by Jordanwb on 2008-08-31
Try the Medibuntu link

---

