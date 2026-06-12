---
title: "samba shares in fstab, only the first on the list works"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by horacle on 2008-12-08
I added 3 samba shares to fstab, after reboot just the first one worked, when I try to access the other 2, I get persmision denied error. If I mount them manually, all of them work, then I changed the order of the shares in the fstab list, and again, I could only browse the first one in the list. 
The fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

//first_share/datos /home/datos smbfs auto,username=myuser,password=mypassword,uid=1000,umask=000,user   0 0
//second_share/driveD/efianza /home/efianza smbfs auto,username=myuser,password=mypassword,uid=1000,umask=000,user   0 0
//third_share/warehouse /home/warehouse smbfs auto,username=myuser,password=mypassword,uid=1000,umask=000,user   0 0

Am I missing something here?

TIA

---

### Post by Iowan on 2008-12-08
I've seen that problem mentioned before (not necessarily for 8.10) - now if I can find it...

I should point out that smbfs is deprecated - cifs has replaced it.  [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a good cifs-mounting How-To.

---

### Post by horacle on 2008-12-08
thank you, checking on cifs now :D

---

