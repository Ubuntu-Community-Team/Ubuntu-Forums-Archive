---
title: "drive update question."
date: 2024-05-15
forum: MINT
---

### Post by isprins on 2024-05-15
Hi, I currently have a 500GB ssd that is used as a boot drive. It also contains my home folder. There's also a 1TB drive that is currently used as storage.
I want to upgrade the 500GB to a 1TB ssd, and put the two 1TB drives in a mirror if possible.

What is the easiest method to accomplish this?

---

### Post by TheFu on 2024-05-15
Which OS?   Which release?
In general, you'll need to reinstall choosing to setup RAID1 before the OS is installed.  But if you don't already have a 100% solid backup and restore method, RAID makes NO sense at all.  There are RAID problems that happen from time to time where the only solution is to wipe everything and start over from backups.  Backups are 1000x more important than RAID.

[LIST]
[*]RAID solves 2 issues.  High-Availability and, if you have a HW-RAID card with a huge cache, you might get better performance.  That's it.  For most users, RAID is a way to write corrupted data to 2 places concurrently.
[*]Backups solve 999 issues.
[/LIST]

BTW, when I switched to SSDs, I stopped using RAID completely.  SSDs are extremely reliably, so if they last 2 months, they will likely last the total time in their warranty.  I'm assuming you aren't buying cheap SSDs and actually get them from vendors that publish TBW requirements for their warranties.  If the "endurance" number isn't on the package and advertised clearly, run away from those vendors.  There are some 5 yr old vendors that don't publish TBW/endurance numbers at all. Those have much higher failure rates.

So, do you have backups working already?  If the SSD in the system failed right now, would you consider it an inconvenience or start freaking out over all the data lost?  If you'd freak out, you have no business considering RAID-anything.  RAID is never a backup.

---

### Post by isprins on 2024-05-15
It's linux mint. Well, I don't have to put it into raid.
Cloning the 500GB drive to a file, switching out the old drive with a new 1TB ssd,  and clone the file to the drive should be enough.

---

### Post by coffeecat on 2024-05-15
*Thread moved to **Mint** sub-forum.*

---

### Post by TheFu on 2024-05-15
> **isprins said:**
> It's linux mint. Well, I don't have to put it into raid.
Cloning the 500GB drive to a file, switching out the old drive with a new 1TB ssd,  and clone the file to the drive should be enough.

I don't know anything about installing Linux Mint.  I've only installed it once and at the time, I selected ZFS as the root file system.  

OTOH, I know much more about installing on Ubuntu with and without RAID, but the different release (yy.mm number!) and exact DE version matters.  For example, in 24.04, I don't think it is possible except in an Ubuntu Server install.  With 20.04, I know it is possible using LVM, I have a play 20.04 LVM install that was setup specifically to test RAID1.  My 22.04 installs aren't RAID, but LVM is supported and should work.   I will say that LVM-RAID is ugly in **lsblk** and **df** output.

You should ask questions like this in the Mint Forum.  They are more knowledgeable about Mint installations there.

I would say you don't really want to clone the whole 500G drive, unless you are comfortable using **gparted** to expand the total storage seen.  Cloning a drive brings the UUIDs and sizes and sector sizes over.  If the old drive is MBR, you should use the as an opportunity to switch the GPT and if it is GPT already, the 2nd partition table will be located in the middle of the storage, not at the end like it should be.  I don't know if gparted can fix that. **gdisk** can, I'm fairly certain.

If it were me, I'd do a fresh install onto the new SSD, then move my data and settings over using my normal data recovery methods that leverage my backups.  When will you have a chance to test your backups without any risk like this?

---

### Post by isprins on 2024-05-15
Of course I have backups.

---

