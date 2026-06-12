---
title: "TestDisk Not supporting APFS File System? (OSX)"
date: 2019-04-18
forum: Mac OSX
---

### Post by shiftescape on 2019-04-18
Have a Mac running OSX Mojave which uses Apple's new APFS file system instead of HFS. 
When I run testdisk on an OSX hard drive that has Mojave on it and try to open a partition with the utility option I get an error that says "Testdisk currently doesnt support this file system" 
I am running Testdisk from a live copy of Ubuntu and the OSX drive is good and bootable. according to Testdisk after analyzing it.
 I just wanted to back up a few files rather than the entire hard drive.  Testdisk will allow me to make an image of the drive, it just wont give me a peak into the directories. 
That being said is there a better way to backup a OSX hard drive through ubuntu? 
The drive came out of a Macbook that has a logic board firmware issue and cant boot. I just wanted to backup the Desktop, Documents, Music and Pictures folder before installing a new logic board in case some how the drive get corrupted in the process.

---

### Post by TheFu on 2019-04-20
"better" is subjective.

If a file system isn't supported, then the only method I know to make a copy is to use a disk imaging tool.  Some of those are:
dd
ddrescue
partimage
clonezilla

These don't work at the file level because they can't understand the file system.  Apple's proprietary walled garden. [https://askubuntu.com/questions/991695/is-it-possible-to-mount-apfs-apples-newest-file-system-in-ubuntu-17-10](https://askubuntu.com/questions/991695/is-it-possible-to-mount-apfs-apples-newest-file-system-in-ubuntu-17-10) has something, but I'd stay with bit-for-bit copies at this point.

You should complain to Apple or take the device into an Apple storage to have them fix it.  May want to consider using a more compatible file system.

---

### Post by shiftescape on 2019-04-20
> **TheFu said:**
> "better" is subjective.

If a file system isn't supported, then the only method I know to make a copy is to use a disk imaging tool.  Some of those are:
dd
ddrescue
partimage
clonezilla

These don't work at the file level because they can't understand the file system.  Apple's proprietary walled garden. [https://askubuntu.com/questions/991695/is-it-possible-to-mount-apfs-apples-newest-file-system-in-ubuntu-17-10](https://askubuntu.com/questions/991695/is-it-possible-to-mount-apfs-apples-newest-file-system-in-ubuntu-17-10) has something, but I'd stay with bit-for-bit copies at this point.

You should complain to Apple or take the device into an Apple storage to have them fix it.  May want to consider using a more compatible file system.
After digging deeper it looks like not even Apples older os’s support APFS. If you upgrade to High Sierra or Mojave your drive is converted to APFS and nothing will read your drive but those two OS’s. Also APFS OS can’t read HFS either so it’s almost like they should be actually OSXI instead of OSX Since they aren’t compatible with any other OSX’s. 
I assume eventually updates will happen that will allow for data recovery for APFS in TestDisk and others, but until then it looks like to recover data your stuck paying money for a dedicated file recovery program.

---

