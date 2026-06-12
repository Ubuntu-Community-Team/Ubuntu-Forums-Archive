---
title: "Ubiquity confused about /target"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by recluce on 2011-03-06
Once again, I tried to install natty. After the install from a USB key failed at about 75% on alpha1 and alpha2, failed at 25% on alpha3, I finally installed from DVD. Before you ask, the MD5s of everything were checked, the DVD verified.

Installing from the Live desktop, I tried to install to /dev/sdc10 (root) and /dev/sdc9 (home), on the following disk layout:

```

/dev/sdc1  vfat     DellUtility         
/dev/sdc2  vfat     WINDOWS SYSTEM/BOOT
/dev/sdc4  reiserfs GRUB (not in use)
/dev/sdc3  extended
  /dev/sdc5  ntfs     Windows XP
  /dev/sdc6  ntfs     Windows Data  
  /dev/sdc7  reiserfs Jaunty
  /dev/sdc8  swap     swap area
  /dev/sdc9  ext4     Natty
  /dev/sdc10 ext3     home

```

While trying to figure out where to import user settings from, the migration assistant set /target to /dev/sdc2. It failed to do anything, as it could not find a valid NTFS signature - small surprise, since that partition is vfat!

Next, ubiquity tried to unmount /target/home, which did not exist and the installer stopped with a crash message. At this point, /target was still my Windows vfat boot partition!

Here the relevant segment from SYSLOG:

```

Mar  6 04:19:39 ubuntu migration-assistant: info: setting ostype from: '/dev/sdc2:Windows NT/2000/XP (loader):Windows2:chain'
Mar  6 04:19:39 ubuntu migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/target'
Mar  6 04:19:39 ubuntu ubiquity: NTFS signature is missing.
Mar  6 04:19:39 ubuntu ubiquity: Failed to mount '/dev/sdc2'
Mar  6 04:19:39 ubuntu ubiquity: : Invalid argument
Mar  6 04:19:39 ubuntu ubiquity: The device '/dev/sdc2' doesn't seem to have a valid NTFS.
Mar  6 04:19:39 ubuntu ubiquity: Maybe the wrong device is used? Or the whole disk instead of a
Mar  6 04:19:39 ubuntu ubiquity: partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
Mar  6 04:19:39 ubuntu migration-assistant: info: Mounting /dev/sdc2 to /target with NTFS failed.
Error: Could not find the path /target/WINDOWS/system32/config/software
Error: Could not find the path /target/WINNT/system32/config/software
Fatal: Could not find the SOFTWARE registry hive at /target/WINNT/system32/config/software.
Mar  6 04:19:39 ubuntu ubiquity[3951]: migration-assistant: filtering out Windows 7 (loader) (/dev/sdb1) as it has no users
Mar  6 04:19:39 ubuntu ubiquity[3951]: migration-assistant: filtering out Windows NT/2000/XP (/dev/sdc1) as it has no users
Mar  6 04:19:39 ubuntu ubiquity[3951]: migration-assistant: filtering out Windows NT/2000/XP (loader) (/dev/sdc2) as it has no users
Mar  6 04:19:39 ubuntu ubiquity[3951]: switched to page migrationassistant
Mar  6 04:20:14 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Mar  6 04:20:14 ubuntu ubiquity: umount: /target/home: not found

```

In other words, /target was set to a wrong partition at that point. Should I be glad the installer crashed, instead of causing additional damage to a partition where it had no business doing anything in the first place? Why can't the installer get the difference between vfat and NTFS right?

I never had comparable problems before, what the hell is wrong with natty's installer? Any helpful suggestions? Should I post this as a bug on launchpad?

BTW: PLEASE, no replies that natty works for you. I believe you, but it doesn't help me one bit.

---

### Post by cariboo on 2011-03-06
I seem to recall that there were problems with the migration assistant, have you tried to install without using the migration assistant? Also did you check to see if /target/home actually existed?

/target is chrooted during the install process, once the install is finished, and you reboot, it becomes the main file system, so there isn't anything to worry about when it mounts a windows partition in order to migrate your settings.

btw what is on /dev/sda and /dev/sdb?

---

### Post by recluce on 2011-03-06
> **cariboo907 said:**
> I seem to recall that there were problems with the migration assistant, have you tried to install without using the migration assistant? Also did you check to see if /target/home actually existed?


How Do I install without the migration assistant?

Maybe I did not word this clearly, but /target continued to point at /dev/sdc2 (the vfat Windows system partition), even after the installer crashed with a message that it could not write to /target.

So yes, /target did exist, but pointed were it really shouldn't.

> **cariboo907 said:**
> 
/target is chrooted during the install process, once the install is finished, and you reboot, it becomes the main file system, so there isn't anything to worry about when it mounts a windows partition in order to migrate your settings.

btw what is on /dev/sda and /dev/sdb?

/dev/sda and /dev/sdb are two SSDs, one has Lucid, the other Windows 7 (I really don't want to use these to play around). If you believe it helps, I will gladly post fdisk or blkid output for these drives.

---

### Post by cariboo on 2011-03-06
/target will always exist during an installation, it just the sub-directories under /target I was curious about. I never use the migration assistant, as I have a separate /home/cariboo directory, I usually delete all the hidden configuration files and directories except for ~/.thunderbird and I leave what ever is in Documents, Music, Pictures and Downloads where they are for a fresh install. 

I was also curious why /dev/sda and /dev/sdb didn't show up in your listing. I guess I'm just being nosey. :)

---

### Post by recluce on 2011-03-06
> **cariboo907 said:**
> /target will always exist during an installation, it just the sub-directories under /target I was curious about. I never use the migration assistant, as I have a separate /home/cariboo directory, I usually delete all the hidden configuration files and directories except for ~/.thunderbird and I leave what ever is in Documents, Music, Pictures and Downloads where they are for a fresh install. 

I was also curious why /dev/sda and /dev/sdb didn't show up in your listing. I guess I'm just being nosey. :)

I leave the /home untouched, too. Sure /target always exist, but it is pointing the wrong way. Can you tell me how to start the install without the migration assistant?

---

### Post by recluce on 2011-03-11
*** BUMP ***

Any helpful input, anyone?

(I begin to believe that I should just forget about Natty...)

---

### Post by cariboo on 2011-03-11
There has been at least one show-stopper bug in ubiquity recently, it may be wise to hold off until at least that bug, which may be a part of your problem, is fixed. Bug #[lpbug]730209[/lpbug]

---

### Post by recluce on 2011-03-14
> **cariboo907 said:**
> There has been at least one show-stopper bug in ubiquity recently, it may be wise to hold off until at least that bug, which may be a part of your problem, is fixed. Bug #[lpbug]730209[/lpbug]

I guess I will give it another shot with beta1 then. Thanks...

---

