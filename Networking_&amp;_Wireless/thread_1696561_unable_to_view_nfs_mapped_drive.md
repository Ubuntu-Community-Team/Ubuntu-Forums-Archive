---
title: "unable to view nfs mapped drive"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by avatardvr@gmail.com on 2011-02-27
help.  newly installed harddrive shared via nfs on an Ubuntu 10.10 machine to another Ubuntu 10.10 machine.  have 3 harddrives mounted in /media and have /media exported.  two of the drives are viewable but the new drive I cannot see data over nfs.  blank page.  chown user chmod etc, I believe the permissions are set up correct, comparing to another accessible drive they seem to be identical.  Any help on this would be greatly appreciated.

---

### Post by Jose Catre-Vandis on 2011-02-27
Try exporting the drive by itself, rather than through /media.

So for example say your drive is at 192.158.0.2 - /dev/sdc and your directory to share is /media/myfiles

in /etc/fstab you would have something like:
```
/dev/sdc1       /media/myfiles            ext3    defaults        0       0
```
then in your exports file something like:
```
/myfiles 192.168.0.1/24(rw,no_root_squash,async,no_subtree_check)
```
then on your client for the mount point:
```
sudo mkdir /media/myfiles
```
and mount:
```
sudo mount 192.168.0.2:/media/myfiles /media/myfiles
```

My server has 4 x HDD set up in this way, works well

---

### Post by avatardvr@gmail.com on 2011-02-27
Yup, that worked.  Thanks for the quick response Jose.  Any idea why I wasnt able to view just that one drive when I mapped my media folder but am able to view it when its mapped on its own?  Again, thanks for your help.

---

### Post by Jose Catre-Vandis on 2011-02-28
I really don't know :(  When I first tried with mutiple drives I had the same problem as you, then went at it the way as described above and it worked, so I just gave thanks and moved on :)

---

