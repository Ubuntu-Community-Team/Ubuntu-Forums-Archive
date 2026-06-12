---
title: "[SOLVED] Recover data on files on MacBook"
date: 2008-05-13
forum: Mac OSX
---

### Post by rmtatum on 2008-05-13
I accidentally deleted some files off someone's MacBook.  I attempted to change the write permissions on a usb flash drive by typing ```
chmod -R 777 *
```.  (I later found out that the write protect lock was on the drive.).  Well, the purpose of changing the permissions was so I could delete some files from the drive (I let someone borrow my flash drive, and she wanted to delete some files).  I think I closed the terminal window and then later opened a new by clicking on the terminal icon on the dock (the window was closed, but the application was still open.).  Thinking that I was still in the flash drive's directory, I typed ```
rm -rf *
```.  Once I noticed files disappearing from the desktop, I quickly pressed CTL-Z to stop rm from running.  Is there a free application I can use to recover the missing files? (Also, I managed to somehow mess up the write permissions on the files.)  Is there a live linux cd that could recover files from a Mac?

---

### Post by MONODA on 2008-05-13
ok first thing you do is stop using your mac, keep it off and use another computer. When you tell and OS to delete files, it doesnt really delete them, it just marks them as available space and then other files can be written over that space. If you are using leopard, I dont think that there is any way to get you files back since once you click delete in leopard, it replaces the files with pseudo files. Try googling around for some recovery apps.

---

### Post by rmtatum on 2008-05-13
The MacBook is not in use and I believe it is running Tiger.  Most of the recovery applications I have found require installation on the host computer.  However, I can't write any data to the hard drive.

---

### Post by rmtatum on 2008-05-13
I found a way to recover the files.

A possible solution is to boot the MacBook in Targeted Disk Mode and connect it to a PC.  From there I can run Steve Gibson's Spinrite and recover the deleted files.  (However, the owner of the computer has decided to take the machine at a computer shop.)

---

### Post by az on 2008-05-15
> **rmtatum said:**
> I found a way to recover the files.

A possible solution is to boot the MacBook in Targeted Disk Mode and connect it to a PC.  From there I can run Steve Gibson's Spinrite and recover the deleted files.  (However, the owner of the computer has decided to take the machine at a computer shop.)

Boot ubuntu-rescue-remix and undelete or file-carve your file.

Spinrite will not recover deleted files.  Spinrite does nothing that S.M.A.R.T. can't do and your drive has S.M.A.R.T. built into it.  Spinrite tries to get around read-errors.  You have a delted file, not a physical problem with your drive.

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

### Post by rmtatum on 2008-05-15
> **az said:**
> Boot ubuntu-rescue-remix and undelete or file-carve your file.

Spinrite will not recover deleted files.  Spinrite does nothing that S.M.A.R.T. can't do and your drive has S.M.A.R.T. built into it.  Spinrite tries to get around read-errors.  You have a delted file, not a physical problem with your drive.

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

Steve Gibson's website for Spinrite states that it has a technology called Dynastat, which can be used for data recovery.

---

### Post by az on 2008-05-16
Spinrite is not a data recovery tool.  

Spinrite is something you try when you don't want to buy a new hard drive and want to keep using your old broken hard drive.  

It cannot undelete a file.

---

### Post by pacificial on 2008-10-01
Hi,


Few times ago, i have faced same problem. Someone suggested me to use Stellar Phoenix Macintosh data recovery software. I tried this software and with the help of this i recovered my lost data. You can also try this [Data recovery Mac ]("http://www.macintosh-data-recovery.com")software to recover data from Macbook.

---

### Post by shadowdude1794 on 2008-11-28
Not sure if it would work, but maybe you could hook the Mac drive up to a Windows machine (if you aren't concerned about voiding your warranty), and use Recuva (assuming you have drivers for hfs+).

Any one know if this would work?

---

