---
title: "Nautilus and ls give different listings on SMB mount point"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by jannewmarch on 2011-04-28
Mounting a Windows SMB share by

    sudo mount -t cifs //bhtdata/infostore /G -o username=******,password=******

An ls of /G shows an expected listing of files on the share:
  5mb-file.bin
  Academic Planning and Research
  Applied Design in Industry
  AppLog_Jan21_2004.evt
  Automotive, Transport & Engineering
  BDGM
  Bookshop
  Buildings & Properties
  Centre for Biotechnology and Animal Sciences
  Centre for Building and Furniture Studies
  ....

Nautilus navigating to the same directory shows quite unexpected and different results as in the attached png file.

Using Ubuntu 10.10 with Nautilus 2.32.0

---

