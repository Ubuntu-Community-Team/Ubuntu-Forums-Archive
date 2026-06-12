---
title: "Can't get my music to show up"
date: 2008-05-26
forum: Multimedia Software
---

### Post by TXJBAR on 2008-05-26
I new to ubuntu 7.10, and i have done all the following steps to try and get my music files (mostly mp3's) to show up from my ext HDD:


Quote:
Installing codec on Ubuntu 8.04
System> Administration > Synaptic Package Manager and install all gstreamer

Install w32codecs and libdvdcss2
Support for WMV, RealMedia and other formats has been bundled into the w32codecs package. This package is not available from the Ubuntu repositories due to licensing and legal restrictions.
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
Then, add the GPG Key using the following commands
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update

For i386 Users install Codecs using the following command
sudo apt-get install w32codecs libdvdcss2


after doing this i still get nothing, all my pictures and other files appear from the drive but no music. Can anybody help me on this? Thanks

---

### Post by TXJBAR on 2008-05-26
Nevermind, my ext HDD was having issues.

---

