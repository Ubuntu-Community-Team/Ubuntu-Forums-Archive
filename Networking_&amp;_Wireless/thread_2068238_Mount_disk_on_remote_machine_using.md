---
title: "Mount disk on remote machine using"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by rjvencken on 2012-10-08
(machines A and B both 10.04)
First /dev/sda1 is mounted in /media/big on machine A through fstab
Then it's shared through "Sharing options" which makes it available on machine B: Places > Network > A > Windows Shares > Big
Now I'd rather have it mounted in B on startup. I'm assuming this should be an entry in fstab but I can't find a decent example.

Putting this line in /etc/fstab:
**//192.168.2.1/media/big /media/scratch cifs user=admin01,password=*************
Then:
**sudo mount -a**
Gives me:
**mount: //192.168.2.1/media/big is not a valid block device**

---

### Post by redmk2 on 2012-10-08
> **rjvencken said:**
> (machines A and B both 10.04)
First /dev/sda1 is mounted in /media/big on machine A through fstab
Then it's shared through "Sharing options" which makes it available on machine B: Places > Network > A > Windows Shares > Big
Now I'd rather have it mounted in B on startup. I'm assuming this should be an entry in fstab but I can't find a decent example.

Putting this line in /etc/fstab:
**//192.168.2.1/media/big /media/scratch cifs user=admin01,password=*************
Then:
**sudo mount -a**
Gives me:
**mount: //192.168.2.1/media/big is not a valid block device**

Since you are mounting the share remotely; the format for all smb (cifs) resources is //ip_address/SHARE_NAME.  Use the share name not the /path to the share.  The path is only relevant to the local host OS.

---

### Post by rjvencken on 2012-10-08
> **redmk2 said:**
> Since you are mounting the share remotely; the format for all smb (cifs) resources is //ip_address/SHARE_NAME.  Use the share name not the /path to the share.  The path is only relevant to the local host OS.
Yes!! It's working. Thank you!

---

