---
title: "Mount Buffalo NAS"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by mwdowns on 2010-07-24
Hello folks.

I'm trying to edit my fstab so that folders from my Buffalo LS-CH1.0TL NAS will be mounted every time I boot into Ubuntu.

These are the entries I have in my fstab:```
//192.168.3.2/usbdisk1						/mnt/Music 	     cifs 	user,defaults 	      0 0
//192.168.3.2/Movies						/mnt/Movies 	     cifs 	user,defaults 	      0 0
//192.168.3.2/TV						/mnt/TV 	     cifs 	user,defaults 	      0 0
```

However, that is not working.  I made the folders in the /mnt directory, but there is nothing in them.

What should my fstab look like so that these shares will be mounted?

Thanks.

---

### Post by Iowan on 2010-07-25
A few How-To's that *might* help:
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")
[http://ubuntuforums.org/showthread.php?t=1186877]("http://ubuntuforums.org/showthread.php?t=1186877")

---

