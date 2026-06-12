---
title: "Please help me! I can't boot!"
date: 2019-07-12
forum: MINT
---

### Post by tombstoner2 on 2019-07-12
I can't boot into my computer! I stupidly deleted a partition I shouldn't have and now I am getting the error about there being a minimal BASH-like lines available. I booted my computer to legacy mode and I was able to get in that way using a live CD, and I tired boot-repair. It was going ok until the end when it told me that I had to have it in EFI mode. I made a log so you can see what is wrong. I would appreciate any help I can get. I don't know a lot about Linux, just had 1 class. Here is my log: [http://paste.ubuntu.com/p/NQHHKYcnZ8/](http://paste.ubuntu.com/p/NQHHKYcnZ8/) I don't care about DeepIn being gone. I was just testing that OS out. Please help me! I am lost without my computer! Thank you!!
Lisa

---

### Post by oldfred on 2019-07-13
Do you have Ubuntu or just Mint & Deepin?

Can you not directly boot from UEFI boot menu.

You need to boot live installed in UEFI mode to repair in UEFI mode.
And since system & installs are all UEFI, you never should be booting in BIOS/CSM/Legacy mode.

Only a small part of grub is in the ESP - efi system partition. And rest is in the / (root) partition. So if you delete the partition that is the default boot, then you have no grub menu. 
But with UEFI other installs are or should be still there and bootable directly from UEFI boot menu when in UEFI boot mode.

UEFI boot mode is usually a setting in UEFI, f2 or del key to get to settings. But booting flash drive is separate and normally has two boot options for install/repair flash drives. One UEFI:flash and one flash where flash is name or label of flash drive. My system says UEFI:pmap or pmap.

---

### Post by oldrocker99 on 2019-07-13
Personally, every UEFI installation I have tried has failed to install grub, leaving . Legacy boot, on the other hand, always has worked for me.

Just sayin'.

There are 10 kinds of people in the world, those who know binary, and those who don't.

---

### Post by tombstoner2 on 2019-07-13
Hi thanks for the replies. I had Linux Mint and Deepin installed. I could not boot from UEFI at all. I finally just said to heck with it and I was able to reinstall Mint in CSM mode. It gave me a bootloader then but still wouldn't load without the Live CD. I went in and tried to reinstall Linux again and it gave me the option to switch to UEFI mode when I was performing the installation. So now I'm up and running but lost everything in the process. Now I'm trying to install some of my old programs but I have a problem now with one of the packages. Should I install it here or just post at the Linux Mint forum?

"The package fruho:i386 needs to be reinstalled, but I can't find an archive for it." (the 64 package wouldn't work either so I tried this one.)

I also get "package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal"

but I can't reinstall it.

---

### Post by oldfred on 2019-07-13
Moved to Mint sub-forum as not Ubuntu.

Your backup procedure should include all of /home and export a list of installed applications to make it easy to get back to exactly where you were.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery
      [/URL]
 Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)
[https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc](https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc) 
    

I just have desktop, so backup my data is most critical. I backup to flash drives & DVDs. I use rsync to flash drives any other drives.
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997) 

[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]
[/URL]

---

