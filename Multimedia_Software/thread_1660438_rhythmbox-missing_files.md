---
title: "rhythmbox-missing files??"
date: 2011-01-05
forum: Multimedia Software
---

### Post by adduds on 2011-01-05
Just a quick rhythmbox question:

For example: 

first boot up my computer open up rythmbox my whole hard drive that i use for music just comes up as missing files until i go to places click on it and shows up on my desktop?

does this have to do with mounting the hd on startup?

---

### Post by adduds on 2011-01-05
bump

---

### Post by adduds on 2011-01-07
bump

---

### Post by jean noel on 2011-01-07
> **adduds said:**
> bump

Are your music files on a separate  partition? 
If so, you will have to mount them if you want rhythmbox to find them. After a hard disk failure, I moved my whole music folder on a second hard disk. 
I have to mount the drive before my music is found. Annoying, but easily done.
Jean Noel

---

### Post by adduds on 2011-01-07
can i do this on bootup as part of start up?

---

### Post by Linyx on 2011-01-07
> **adduds said:**
> can i do this on bootup as part of start up?

You have to mount that Drive(which contain your music) on boot-up....You can simply do it via Editing FSTAB.....

You can do it through easy GUI-TOOLS as well > [http://www.dedoimedo.com/computers/automount_ntfs.html](http://www.dedoimedo.com/computers/automount_ntfs.html)
                                                 
                                                                                      > [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

But i will suggest you to manually EDIT your FSTAB for Auto-mounting.................

---

### Post by adduds on 2011-01-07
ty i manually edited my fstab ..

question on why it partially worked...

originally i was writing

```
/dev/sda   /media/sda  ntfs   defaults   0   0
```

```
Disk [COLOR="Red"]/dev/sda[/COLOR]: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xadadadad

   Device Boot      Start         End      Blocks   Id  System
[COLOR="red"]/dev/sda1[/COLOR]               1      121601   976760001    7  HPFS/NTFS

```

then

```

toews@desktop:~$ sudo mount -a
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

So i used this

```
/dev/sda1   /media/sda  ntfs   defaults   0   0
```

Now i can sudo mount -a without error but when i open rhythmbox i still get "missing files" until i double click on the all_media on my desktop.....

weird thing is though i can play my music from the harddrive in rhythmbox but it doesn't show the music i've created in playlists.....

thanks for the help

---

### Post by Linyx on 2011-01-08
The Partition for which you had add a line in [SIZE=2]fstab[/SIZE] was Auto-mounting ....?In this case /dev/sda1....

Edit:- Post the output of

                              ```
sudo blkid
```

Also
                              ```
sudo fdisk -l
```

---

### Post by adduds on 2011-01-08
```
toews@desktop:~$ sudo blkid
[sudo] password for toews: 
[COLOR="Red"]/dev/sda1: LABEL="all_Media" UUID="50FC2F99FC2F787C" TYPE="ntfs" 
[/COLOR]/dev/sdb1: UUID="DE281C19281BEF71" TYPE="ntfs" 
/dev/sdb5: UUID="1e4c3dc0-2e96-44d2-beb4-fcec826014cc" TYPE="ext4" 
/dev/sdc1: LABEL="My Passport" UUID="6258-7DA7" TYPE="vfat" 
```

```
toews@desktop:~$ sudo fdisk -l

Disk [COLOR="Red"]/dev/sda[/COLOR]: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xadadadad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x067b70a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12163    97699266    7  HPFS/NTFS
/dev/sdb2           12164       24322    97657857    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sdb5           12164       24322    97657856   83  Linux

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x358d73c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)

```

---

### Post by Linyx on 2011-01-09
Is your drive Auto-mounting...?you didn't answer....

**Replace** the line which you had added in fstab on the below given line....its better to mount the Drive by it UUID....

```
[COLOR=Black]dev/disk/by-uuid/50FC2F99FC2F787C /media/all_media ntfs defaults,utf8,umask=007,uid=1000,gid=1000 0 1[/COLOR]
```[SIZE=1]
Just Copy and paste this line so that you won't mistake....Save it & Reboot.

And see if that disk is mounting at Boot or not...?
[/SIZE]

---

### Post by adduds on 2011-01-09
> **Linyx said:**
> Is your drive Auto-mounting...?you didn't answer....

**Replace** the line which you had added in fstab on the below given line....its better to mount the Drive by it UUID....

```
[COLOR=Black]dev/disk/by-uuid/50FC2F99FC2F787C media/all_media ntfs defaults,utf8,umask=007,uid=1000,gid=1000 0 1[/COLOR]
```
[SIZE=1]
Just Copy and paste this line so that you won't mistake....Save it & Reboot.

And see if that disk is mounting at Boot or not...?
[/SIZE]

my harddrive is listed in places immediately on bootup but doesn't not appear on the desktop until i go to places and click on it....if that tells you anything 

during boot up there was an error and said s for skip or m for manual mounting did manual brought me to a terminal didn't wtf to do so ctrl+d outta that kept booting up when in the os opened rhytmbox and import errored every mp3 on my hd

removed your line from fstab and mine right back to scratch now

---

### Post by Linyx on 2011-01-10
Post your fstab here....

---

### Post by adduds on 2011-01-10
I commented the /dev/sda1 because it didn't work

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb5 :
UUID=1e4c3dc0-2e96-44d2-beb4-fcec826014cc	/	ext4	errors=remount-ro	0	1


#Entry for /dev/sda1 :
#dev/disk/by-uuid/50FC2F99FC2F787C media/all_media ntfs #defaults,utf8,umask=007,uid=1000,gid=1000 0 1


```

---

### Post by Linyx on 2011-01-11
Replace that line with this one....I hope it will now fix...

```
[COLOR=Black]dev/disk/by-uuid/50FC2F99FC2F787C /media/all_media ntfs defaults,utf8,umask=007,uid=1000,gid=1000 0 1[/COLOR]
```

Note:-The Line Which you had added in fstab(as in above post), you had "**#default**" which is incorrect, just copy and paste above line so that you won't mistake....


Good-Luck

---

### Post by adduds on 2011-01-11
old chap i believe we've done IT!!! ty for your patience.....

sorry the dumb mistakes

whats all that stuff mean?

mainly this stuff

```
defaults,utf8,umask=007,uid=1000,gid=1000 0 1
```

i assume spacing and all that is very important

---

### Post by Nightslay on 2011-01-11
whats all that stuff mean?

mainly this stuff

```
defaults,utf8,umask=007,uid=1000,gid=1000 0 1
```i assume spacing and all that is very important[/QUOTE]
 
first part: defaults,utf8,umask=007,uid=1000,gid=1000
is mount parameters

in af normal environment
uid=1000 =userid=1000.(first normal user created is normal id=1000. next userid=1001
gid=1000 = groudid=1000 (same as above just with groups)

sry cant remember the "0 0" in the end of line. something with backup(systemdump) and more.

---

### Post by Linyx on 2011-01-11
> **adduds said:**
> old chap i believe we've done IT!!! ty for your patience.....

sorry the dumb mistakes

whats all that stuff mean?

mainly this stuff

```
defaults,utf8,umask=007,uid=1000,gid=1000 0 1
```i assume spacing and all that is very important

Yes the spaces is Must,,

I think  the other question is Cleared by [Nightslay....]("http://ubuntuforums.org/member.php?u=860275")

For more information, see the full view of "What is fstab & Howto" > [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

