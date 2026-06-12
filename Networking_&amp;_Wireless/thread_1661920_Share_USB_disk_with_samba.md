---
title: "Share USB disk with samba"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by simba71 on 2011-01-07
I've installed ubuntu 10.10 and shared with samba a folder of the disk with no problem
I tryed to share 2 different usb disk and I got problems!

With windows I can see the shares, but not browse and all the setting in smb.conf are the same for the folder in the hard drive and the USB disk

Can you help me?
thank

---

### Post by kgas on 2011-01-07
mount your usb(any external hard disk) under one of the folder of samba share.

---

### Post by Morbius1 on 2011-01-07
The usb sticks are automounting with owner=your-user-name and with permissions pf 0700 meaning only you can access it. If you set the share to allow guests to access it, guests does not = you.

Add the following line to the share definition section on smb.conf to create a mask that will convert the remote guest to your-user-name:
```
force user = your-user-name
```Then restart samba:
```
sudo service smbd restart
```

EDIT: I'm making the assumption that the USB sticks are formatted in FAT32 or NTFS.

---

### Post by simba71 on 2011-01-07
thank it works!

---

