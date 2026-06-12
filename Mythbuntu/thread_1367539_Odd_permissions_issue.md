---
title: "Odd permissions issue"
date: 2009-12-29
forum: Mythbuntu
---

### Post by bcgrown on 2009-12-29
I'm using a fresh install of MythBuntu 9.10 with the default user settings.

The PC is set to autologin and start MythFrontend as user "dave" that I set up during the install.

When I rip a DVD it gets saved to /media/hugevat/Videos with owner dave:dave and permissions 0644.

If I go into the media library and try to delete a ripped DVD, it just says "unable to delete file."

My media library also includes /media/hugevat/Downloads.

If I copy the ripped dvd to /media/hugevat/Downloads, without changing any permissions, the media library is able to delete it.

Permissions for both dirs are exactly the same:
```
dave@videomatic:/media/hugevat$ stat Downloads/
  File: `Downloads/'
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 806h/2054d	Inode: 17113089    Links: 3
Access: (0775/drwxrwxr-x)  Uid: (  103/  mythtv)   Gid: (  105/  mythtv)
Access: 2009-12-29 13:41:57.000000000 -0800
Modify: 2009-12-29 13:42:09.000000000 -0800
Change: 2009-12-29 13:42:09.000000000 -0800

dave@videomatic:/media/hugevat$ stat Videos/
  File: `Videos/'
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 806h/2054d	Inode: 6152193     Links: 2
Access: (0775/drwxrwxr-x)  Uid: (  103/  mythtv)   Gid: (  105/  mythtv)
Access: 2009-12-29 13:28:19.000000000 -0800
Modify: 2009-12-29 13:26:53.000000000 -0800
Change: 2009-12-29 13:26:53.000000000 -0800

```

The same thing happens if I create a dummy ISO file with a "touch test.iso" command.

So... What the heck is going on?

---

### Post by kja999 on 2009-12-30
What about other basic tests ?
Can you touch a file and delete it ?

Also, when you copy to the downloads folder, is this on the terminal as user dave (I.e. cp * ../Downloads/), or using a file manager ?

---

### Post by SiHa on 2009-12-30
Permissions 644 equates to -rw-r--r--, so only root can delete the file. When you copy the file, the copy presumably gets created with permissions 664, or something at least with write permissions for 'Dave'.
What happens if you chmod 666 or 664 the rip in /media/hugevat/Videos?

---

### Post by bcgrown on 2009-12-30
All the file manipulations are on the terminal as user dave (via SSH, but I don't believe that should make any difference)

```
dave@videomatic:/media/hugevat/Downloads$ touch Downloads_test.iso
dave@videomatic:/media/hugevat/Downloads$ touch ../Videos/Videos_test.iso

dave@videomatic:/media/hugevat/Downloads$ stat Downloads_test.iso 
  File: `Downloads_test.iso'
  Size: 0         	Blocks: 0          IO Block: 4096   regular empty file
Device: 806h/2054d	Inode: 17113091    Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/    dave)   Gid: ( 1000/    dave)
Access: 2009-12-30 08:16:00.000000000 -0800
Modify: 2009-12-30 08:16:00.000000000 -0800
Change: 2009-12-30 08:16:00.000000000 -0800

dave@videomatic:/media/hugevat/Downloads$ stat ../Videos/Videos_test.iso 
  File: `../Videos/Videos_test.iso'
  Size: 0         	Blocks: 0          IO Block: 4096   regular empty file
Device: 806h/2054d	Inode: 6152196     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/    dave)   Gid: ( 1000/    dave)
Access: 2009-12-30 08:16:07.000000000 -0800
Modify: 2009-12-30 08:16:07.000000000 -0800
Change: 2009-12-30 08:16:07.000000000 -0800
```

After that, mythfrontend will delete "Videos_test.iso" but not "Downloads_test.iso."

It will delete Videos_test.iso if it's chmodded to 666, but not 664.  This doesn't make any sense to me.

Why can it delete a "644" file in Downloads but not in Videos?

---

### Post by bcgrown on 2009-12-31
Deleted and recreated the "Videos" dir and all is well.

Still have no idea what happened.

---

