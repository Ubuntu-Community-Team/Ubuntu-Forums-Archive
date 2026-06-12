---
title: "FAT32 Disk writer corrupts files?"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ozorba on 2010-09-30
I have a dual boot system and have been using a FAT32 to exchange files between Ubuntu Maverick and Win XP. I saved a small text file in the FAT32 partition when I was using Ubuntu Maverick. I could open and close this file without a problem. However, when I switched over to Win XP the file was not there.

I then did an experiment. I an existing text file  that was created in Win XP while I was in Ubuntu Maverick. I could read that file. I then added additiona text to this file and saved it.

When I tried to ope this file in Win XP it was corrupted. 

I also noticed that when I saved a binary file to FAT32 from Ubuntu Maverick I could not copy/move this file from Win XP. I keep on getting copput file message in Win XP.

Any solutions?

---

### Post by coffeecat on 2010-09-30
To be honest I so rarely use Windows these days that I can't say whether or not I've seen this. But I have recently used a FAT32 formatted external drive to transfer files between Maverick and MacOS in both directions without problem.

Have you tried using a FAT32 formatted USB device instead of your FAT32 partition to exchange files between Ubuntu and XP? If you do this and you do not see this issue then that would suggest that there is something wrong with your FAT32 partition. If you do see the issue then that might suggest a bug with the way Maverick is writing to FAT32 which deserves to be investigated.

One comment: I haven't used a shared FAT32 partition on a Windows/Linux multiboot for 2-3 years. NTFS read-write seems so reliable these days in Ubuntu that it would be a better choice than FAT32. It's more robust than FAT32 and you have Windows available to run chkdsk if you do get filesystem corruption.

---

### Post by dino99 on 2010-09-30
why using Fat32 these days ?

use ntfs, formated with xp tool, on xp side install ifs2ext and ntfsprog on ubuntu side (repo), that it.

---

### Post by ozorba on 2010-09-30
> **dino99 said:**
> why using Fat32 these days ?

use ntfs, formated with xp tool, on xp side install ifs2ext and ntfsprog on ubuntu side (repo), that it.

Historical. 

I have not used a USB external disk to test this yet. I am not keen on Win XP but I have to use it once in a while when the application I use is not available in Linux yet.

---

### Post by cariboo on 2010-09-30
All my flash drives are fat32, I haven't noticed any file corruption, transferring files back and forth between XP and Maverick

---

### Post by lespaul_rentals on 2010-09-30
> **ozorba said:**
> I have a dual boot system and have been using a FAT32 to exchange files between Ubuntu Maverick and Win XP. I saved a small text file in the FAT32 partition when I was using Ubuntu Maverick. I could open and close this file without a problem. However, when I switched over to Win XP the file was not there.

I then did an experiment. I an existing text file  that was created in Win XP while I was in Ubuntu Maverick. I could read that file. I then added additiona text to this file and saved it.

When I tried to ope this file in Win XP it was corrupted. 

I also noticed that when I saved a binary file to FAT32 from Ubuntu Maverick I could not copy/move this file from Win XP. I keep on getting copput file message in Win XP.

Any solutions?

Are you properly mounting and unmounting said volume?

Using the command prompt, try to mount the volume manually, save a file to it, unmount, then restart. I suspect the asynchronous nature of filesystem mounts is causing the problem. I've experienced files (some of them quite small) that take up to a couple minutes to actually be written to the drive. It's not the size of the files that causes this, they are simply added to a queue and pushed to the back burner until the system "can get to it," if you will.

> **ozorba said:**
> I an existing text file

I think you should your /home folder.

---

### Post by 23dornot23d on 2010-09-30
> 
When I tried to open this file in Win XP it was corrupted. 


What program did you use in XP to open it .. did you try others ....

Do you have a copy of the before and after .... of this file ....

Do you run a virus checker ..... did you check the file ....

How many bytes were added to the file ..... 

Can you do it again ...... add one character to the text file  .... save it and see what the file size is before and afterwards .........

Try it with something simple ...... 

AAA in a text file .... add another A

I cannot try to reproduce this as I no longer use windows .....

---

