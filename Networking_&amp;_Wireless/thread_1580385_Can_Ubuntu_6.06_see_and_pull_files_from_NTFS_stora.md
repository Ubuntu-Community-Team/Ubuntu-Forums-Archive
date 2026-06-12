---
title: "Can Ubuntu 6.06 see and pull files from NTFS storage device?"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by geercom on 2010-09-23
I plan to use a laptop running ubuntu 6.06 as a backup work computer. It will be most useful if, when the primary computer is out of commission, I can connect it to the Seagate external hdd, which runs an NTFS file system, and pull files from there, convert them to .RTF etc and work on them.

Is there a way to make this happen?

---

### Post by pedro_orange on 2010-09-23
This should pose no problem.

As long as you can see the filesystem under fdisk -l, you should be able to mount it by editing your /etc/fstab with something like:

```
dev/sda1 /media/NTFS_External ntfs nls=utf8,umask=0222 0 0
```

You will ofc have to change the first bit to reflect what it says in your fdisk -l, and you can change /media/NTFS_External to where you wish to mount the disk in your file system. You can verify it has mounted by running sudo mount -a after doing the above.

---

### Post by geercom on 2010-09-23
I am not a programmer. Is there a simple way that a non-programmer can do it? Like with a special application made for this or something?

> **pedro_orange said:**
> This should pose no problem.

As long as you can see the filesystem under fdisk -l, you should be able to mount it by editing your /etc/fstab with something like:

```
dev/sda1 /media/NTFS_External ntfs nls=utf8,umask=0222 0 0
```

You will ofc have to change the first bit to reflect what it says in your fdisk -l, and you can change /media/NTFS_External to where you wish to mount the disk in your file system. You can verify it has mounted by running sudo mount -a after doing the above.

---

### Post by pedro_orange on 2010-09-23
This is not a programming task. 
This is a case of editing a few simple text files, and using the command line. Do not fear the text!

```
fdisk -l
``` 
This will list all of the file systems on your machine. Find the Windows one you wish to mount, and write down it's information.

Then, simply type in:

```
gksudo gedit /etc/fstab
```
This will open GEdit and open the fstab file for editing. Follow the instructions I said below, and hit save.

Then finally run:

```
sudo mount -a
```

Enjoy.

---

### Post by pricetech on 2010-09-23
You probably want to use a later version than 6.06 though.  Current version is 10.04 LTS with 10.10 rapidly approaching.

---

### Post by geercom on 2010-09-27
I have upgraded to 10.04, thank you for that. How are the strings and instructions different for pulling files from NTFS external hdd if I am using Ubuntu 10.04??

---

