---
title: "mount hard drive"
date: 2010-11-16
forum: Mythbuntu
---

### Post by mythB on 2010-11-16
how do you mount a hard drive with mythbuntu 10.10 i dont know what to do

---

### Post by David Grigor on 2010-11-16
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

covers the topic well. 

When adding to the fstab, I like to use UUID instead of the device name. Mine seems to change order sometimes during boot up and UUID will work everytime.

---

### Post by mythB on 2010-11-16
thank you for the link but thats to much for me to understand, im new with this so i will just leave it alone for now.

---

### Post by Senkoboy on 2010-11-16
Use a program called PySDM. It creates an intuitive GUI to allow you to configure your hard drive partitions, and also includes an assistant to help you choose mounting options that are convenient, such as automatically mounting the partition on startup. This program is a splendid alternative to manually editing the /etc/fstab file

---

