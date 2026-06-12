---
title: "Ubuntu 11.10 MediaTomb NTFS"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by Bad_Monkey on 2011-12-29
I am running ubuntu 11.10 
I have gotten Samba working!
My next problem is MediaTomb
 
The 2 drives with the data i want to stream are both out of a Windows PC
they are NTFS disk.
 
When i try to add the directories with the web gui of mediatomb i get 
Error: could not list directory /media/Server : Permission denied
 
Any thoughts?

---

### Post by foska on 2012-01-14
Sounds as though you need to mount those drives.

First run

```
sudo fdisk -l
```

This tells you information you will need about the drives which are attached to your computer.  You are looking for /dev/sda1, /dev/sda2 and so on.  Note which drive it is you are trying to mount.

create a mount point. I like to create mine in my home directory

```
mkdir directory_name
```

eg. This is an example of how I mounted a USB drive. where sdc1 is the device (usb drive name). USB_DRIVE is a folder created in my home directory and serves as a mount point for the USB drive that I am trying to mount.


```
sudo  mount /dev/sdc1 /home/foska/USB_DRIVE
```


I am not a Linux guru by any stretch of the imagination but this is what I did and it worked!

---

