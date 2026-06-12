---
title: "Samba: Unable to mount location"
date: 2010-09-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-09-23
Below are the errors in the logs.

```
[2010/09/23 10:13:22.454161,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/my movies failed. Permission denied
[2010/09/23 10:13:22.455374,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service my movies, path /media/Media/My Movies
[2010/09/23 10:13:25.990345,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/my music failed. Permission denied
[2010/09/23 10:13:25.991521,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service my music, path /media/Media/
```

The drive is an ntfs drive that I use to share my files between my Ubuntu partition and Windows 7 partition

---

### Post by GalgoLance on 2010-09-23
I've had a problem where my secondary drive would not be recognized by Ubuntu.  Boot drive yes. 

Solution was to unplug the drive and then plug it into a Windows computer.  Somehow it did something to the drive.  I did not write any thing to the drive. just plugged it into a windoze box and booted up the system.  Windoze recognized the drive.  Then powered down, removed drive, reinstalled in Ubuntu, and then the drive was able to be mounted.  I do not know why.  But it worked.

---

### Post by tad1073 on 2010-09-23
edited original post

---

### Post by tad1073 on 2010-09-24
bump

```
[2010/09/24 12:14:31.878368,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service My Movies, path /media/Media/My Movies
```

[http://ubuntuforums.org/showpost.php?p=9881822&postcount=1](http://ubuntuforums.org/showpost.php?p=9881822&postcount=1)

---

### Post by cariboo on 2010-09-24
This bug #[lpbug]645630[/lpbug], even though it's about a printer is probably the same thing.

---

### Post by tad1073 on 2010-09-24
the problem seems to be with permissions, I removed guest ok = yes parameter and I am able to access my shares.

Like I said in my first post, "The drive is an ntfs drive that I use to share my files between my Ubuntu partition and Windows 7 partition."

So the drive being ntfs I am unable to set permission from ubuntu.

Guess I could use the valid users = whoever then add those people to my system.

---

### Post by farmercyst on 2010-09-24
> **tad1073 said:**
> the problem seems to be with permissions, I removed guest ok = yes parameter and I am able to access my shares.

Like I said in my first post, "The drive is an ntfs drive that I use to share my files between my Ubuntu partition and Windows 7 partition."

So the drive being ntfs I am unable to set permission from ubuntu.

Guess I could use the valid users = whoever then add those people to my system.

this worked for me aswell. i was getting "unable to mount windows share" and all i had to do was change guest ok= to "no". i an sharing an ext4 hard drive though.

---

