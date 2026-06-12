---
title: "Unable to &quot;allow executing file as a program&quot; on mounted NTFS partition"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by DodgeV83 on 2010-09-08
Anyone else having this problem?

Anytime I check "allow executing file as a program", or change any other property in the "permissions" tab of properties, it immediately changes back to the default (within 1 second of clicking it).  It won't let me run an executable without changing the flag, but I don't seem to be able to change the flag.

Not an issue with Ubuntu 10.04 or Fedora.

---

### Post by mc4man on 2010-09-08
> It won't let me run an executable without changing the flag, but I don't seem to be able to change the flag.
You should probably be a little more specific - you're trying to run what? and how?
If it's a .exe or .jar then they don't need to have an x bit set, nor can you on  ntfs, you may just to running up against a security policy that's easily overridden.
If it's a text script of some sort, you'll need to transfer to a fs where you can set the bit.
(there was a vfat patch to Udisks disallowing  any executable text file - don't think that applies here though never checked other than on fat volumes

---

### Post by Morbius1 on 2010-09-08
You are trying to change permissions on an NTFS partition through Nautilus? You can't. You can't change ownership or permissions on a Windows Filesytem. Can't do it on Fedora - can't do it on Ubuntu 10.04 or even Ubuntu 0.04. 

The only way you can change permissions on a Windows Filesystem is with a mount or in fstab. If you have this set up to automount then post your fstab:
```
cat /etc/fstab
```

---

### Post by cariboo on 2010-09-08
If you prepend the command with wine eg:

```
wine program_name.exe
```

do your programs start?

---

### Post by DodgeV83 on 2010-09-08
> **cariboo907 said:**
> If you prepend the command with wine eg:

```
wine program_name.exe
```

do your programs start?

Hm, yes this does work (it was an exe file with wine).  When I run it from the command line it works, but when I double click the file from Nautilus I get:

"Blocked: wine start /unix"
```
<filename> is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```

Double clicking the file works in previous versions of Ubuntu and Fedora.  Should I just file a bug report?

---

### Post by mc4man on 2010-09-08
Now that you've created a custom definition (custom command) for wine, right click on any .exe -> properties -> open with. You should see one named just 'wine' in the list
Set that as the default for .exe's and a double left click will work.

---

### Post by seeker5528 on 2010-09-08
For file systems the do not have a concept of executable versus non-executable files, you have to set the option in the mount options, and it's all or nothing.

If you don't have an fstab entry for your NTFS partition, you can use ntfs-config, on the menu at 'System --> Administration --> NTFS Configuration Tool'.

This will set up the basic options for the partition and create an entry in /etc/fstab similar to:

```
/dev/sdb1       /media/HP_PAVILION      ntfs-3g defaults,nosuid,nodev,locale=en_US.utf8 0       0
```

Theoretically, since I have not actually tried it, then all you should have to do is add 'exec' to the mount options:

```
/dev/sdb1       /media/HP_PAVILION      ntfs-3g defaults,exec,nosuid,nodev,locale=en_US.utf8 0       0
```

You don't want to do this for external drives, unless you are content to open a terminal window and type 'sudo mount /dev/whatever'/'sudo umount /dev/whatever' every time you want to mount/unmount the partition. 

Later, Seeker

---

### Post by mc4man on 2010-09-08
> then all you should have to do is add 'exec' to the mount options:
That would also override the new (as of lucid) security policy, the same can be seen if giving a typical fstab entry for cd/dvd drives where by default now .exe's  cannot be executed on cd/dvd's

The only reason for this behavior is the security policy - .exe's do not need to be set as executable to run except  to satisfy the policy.

Better to just reject this policy (**as currently implemented**) and either workaround when needed or remove individually for good as desired (wine, java, cautious-launcher (browser), only takes a few seconds

---

### Post by seeker5528 on 2010-09-09
> **mc4man said:**
> Better to just reject this policy (**as currently implemented**) and either workaround when needed or remove individually for good as desired (wine, java, cautious-launcher (browser), only takes a few seconds

Oops, the first post didn't specify it was an .exe file which led me down a more generic path and the later confirmation that is was an .exe failed to bring me back to a more specific solution.

But in poking around it did bring usermap (ntfs-3g.usermap in ubuntu) to my attention, which might be something I want to experiment with, so it is not a total loss. ;)

[http://linux.softpedia.com/get/System/Hardware/ntfs-3g-Ownership-and-Permissions-Support-40763.shtml](http://linux.softpedia.com/get/System/Hardware/ntfs-3g-Ownership-and-Permissions-Support-40763.shtml)

[http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/](http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/)

Later, Seeker

---

### Post by syed.rakib.al.hasan on 2010-09-09
i am also not able to do  "allow executing file as a program even on FAT32 system"
whether it's .exe file or bash file.... i right-click the file > properties > permission...... then putting the tick for "allow executing file as a program" does not work.... it revers back.


---------------------------------


and with wine applications i happen to have a similar problem.
i have installed wine a long time and things were working fine....... the only alterations that happened was the scheduled regular system updates (i never handpicked what to update..... the system was always allowed to update whatever it can)
and now i come to use my wine and see that it does not work.

```
blocked: wine start /unix
The file '/media/SOFTWARES/Audio Video softs/HJ Split/hjsplit.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```

---

### Post by cariboo on 2010-09-09
There is a program in the repositories called lxsplit, that is fully compatible with the HJSplit utility

---

