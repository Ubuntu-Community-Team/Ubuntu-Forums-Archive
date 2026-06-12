---
title: "Why Does File Browser Display Different Folder Sizes for Windows?"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by HDTimeshifter on 2009-04-05
Why does File Browser display different folder sizes for Windows systems?  I have a 1 GB folder on my Ubuntu system that I copied to an 2 XP PCs and a Vista laptop.  Locally, they all report 1.04 GB folder size and 1325 files.  However, File Browser reports 1325 files, but different sizes for each Windows folder.  It displays 584 MB for one XP box and the Vista laptop, but 444 MB for another XP box.  I was thinking it had something to do with UNIX 512 block size making it roughly 1/2 for the Windows systems, but really don't understand why it reports different sizes for the XP boxes.  I'm running 64-bit Ubuntu 8.10 and XP Pro SP3 on two PCs and 32-bit Vista SP1 on the laptop.

---

### Post by DGortze380 on 2009-04-05
> **HDTimeshifter said:**
> Why does File Browser display different folder sizes for Windows systems?  I have a 1 GB folder on my Ubuntu system that I copied to an 2 XP PCs and a Vista laptop.  Locally, they all report 1.04 GB folder size and 1325 files.  However, File Browser reports 1325 files, but different sizes for each Windows folder.  It displays 584 MB for one XP box and the Vista laptop, but 444 MB for another XP box.  I was thinking it had something to do with UNIX 512 block size making it roughly 1/2 for the Windows systems, but really don't understand why it reports different sizes for the XP boxes.  I'm running 64-bit Ubuntu 8.10 and XP Pro SP3 on two PCs and 32-bit Vista SP1 on the laptop.

Simple Explanation:
The file systems are entirely different.


Complicated Explanation would involve lots of time on wiki studying the workings of ext3 and ntfs and the differences between them

---

### Post by HDTimeshifter on 2009-04-05
But I thought Samba would handle the differences, and also doesn't explain the inconsistency between two fairly identical XP systems.

---

### Post by DGortze380 on 2009-04-06
> **HDTimeshifter said:**
> But I thought Samba would handle the differences, and also doesn't explain the inconsistency between two fairly identical XP systems.

No, Samba is a file sharing protocol. Has no effect on the way the information is stored on your hard disk.

As far as between the windows systems.
Is one formatted as FAT?
Block Size?
Compression?

There are a bunch of possible reasons.

---

### Post by HDTimeshifter on 2009-04-06
The 2 XP PCs are set up pretty much identically - same formatting and all.

---

