---
title: "Samba mounted with cifs or smbfs slow, but gvfs is fast"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by JorisSpekreijse on 2009-07-15
Hello,    

I have this problem regarding samba mounts under Ubuntu 8.04.    

When I copy a file from or to a mounted Windows point, the speed will not go above the 50 kB/s. When a mount this point via the Gnome network locations (it will then be mounted via gnone virtual file system ), the speed is 2 MB/s.    

I found out that gvfs mounts a samba point with cifs.    Does anyone know where I can find the settings Gnome is using or which settings I should alter? Looking on the Internet all I can find is a slow smb connection or not proper working nic. But gvfs does the job more properly.    

Just in case my mount command in fstab is:  loc1 loc2 cifs credentials=file,iocharset=utf8

---

### Post by JorisSpekreijse on 2009-07-15
Solved this issue bij adding the option rsize=4k.
gvfs-info showed that Gnome mounts standard with 4k, and apparently that is speed the Windows machine likes.

---

### Post by damien82 on 2009-08-09
thanks for adding your solution, worked out great for me =)

---

### Post by cannabix on 2009-10-25
When playing music over a shaky wireless connection using smbfs, the music would often skip during playback (same for videos).  I found this topic and tried "rsize=4k" and now it's working great, so thanks for the solution and maybe this will help someone with the same problem.

Using "cat /proc/mounts" I can see that the default was rsize=16384 and with "4k" the rsize shows as 2048 so I assume the 4k is actually misinterpreted.  So I changed it to "rsize=4096" and it still works great so I would recommend that setting. (4096 is supposed to be what Windows likes and my music is served from Windows XP)

Cheers

---

### Post by r7000 on 2010-04-13
This also worked for me.

Setting rsize=4096,wsize=4096 in the mount options fixed my cifs speed issue.


For speeding up slow samba shares changing smb.conf's socket options to the following worked:

socket options = TCP_NODELAY SO_SNDBUF=4096 SO_RCVBUF=4096

---

