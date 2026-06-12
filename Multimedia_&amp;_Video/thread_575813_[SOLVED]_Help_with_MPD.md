---
title: "[SOLVED] Help with MPD"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by krakerjak on 2007-10-14
I could use a little help with MPD.

I have what I think is a permission problem.  I have an external usb harddrive that contains all of my music on it, I have a link in my MPD music directory to the music directory on my HDD.  It is formatted for Windows, and is shared with the other computers (WinXP/Vista) on my network.  I was unable to create a database until I copied a folder from my HDD and placed it into the MPD music directory.  

I am not sure what to do so that the usb HDD can be used as my music directory.  I tried changing the owner of the link, but that didn't work.

Anyone have an idea?
KJ

---

### Post by zAo on 2007-10-14
Try to mount it with mode 555 in your /etc/fstab. (read + execute for everybody)

---

### Post by krakerjak on 2007-10-14
I am really new to linux, how would I go about that?:confused:

---

### Post by nchase on 2007-10-15
/etc/fstab is the location of a file in your linux filesystem

so, to edit it,  you'd type ```
sudo gedit /etc/fstab
```

In this file, under the <options> column for the appropriate device, you'd add ```
umask=555
```

PS -- have you tried editing the mpd conf file to point directly to your external hard drive as the music directory?

---

### Post by krakerjak on 2007-10-15
I don't seem to have an entry in my fstab for the USB Drive.

fstab contents:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=03bc3991-5323-4f02-ad5a-db78f3121e4f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=76eb757f-7f33-4c3e-9f2b-4d9b49ff4c38 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```

I looked in /dev, & the drive I need to set the permissions on is sdb1.

BTW, I did try to edit MPD.conf to reflect my music directory on that drive.  That didn't work either. 

Thanks for the help!
KJ

---

### Post by nchase on 2007-10-15
I'm getting a little outside my area of knowledge, but can you just add an entry into fstab for your external drive?

---

### Post by krakerjak on 2007-10-15
I don't know, I'll look into it.

I do know what happens if you screw up fstab and drop the mask into the wrong drive... You spend a couple of hours getting your system un-screwed.  Chalk it up to another learning experience.:)

Thanks,
KJ

---

### Post by krakerjak on 2007-10-16
OK, I think I've got it.

I added this to fstab:
```
/dev/sdb1    /media/SharedDrive vfat  iocharset=utf8,umask=000  0    0
```

See this link for more info:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

Now if I can just get MPD & Icecast to start correctly at bootup...

Thanks to all who helped out!
KJ

---

