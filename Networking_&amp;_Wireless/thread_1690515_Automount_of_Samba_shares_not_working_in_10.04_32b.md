---
title: "Automount of Samba shares not working in 10.04 32bit"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by EarlsFurniture on 2011-02-18
[FONT=Lucida Sans Unicode]I'm having an automount problem on Ubuntu 10.04 32bit.  The  smb  shares will not mount on login, and I   have to use:
[/FONT]
```
sudo mount -a
```[FONT=Lucida Sans Unicode](and enter the password for each share,  rather than just once, very odd)

Here's a sample share mount from fstab. (I have six of these)[/FONT] [FONT=Lucida Sans Unicode]
[/FONT] 
```
# share-name on /mnt/samba/share-name
//serverIP/share-name /mnt/samba/share-name smbfs defaults    0    0 
```[FONT=Lucida Sans Unicode]Note, I also can't use the server 'name' but rather am forced to use the IP address for this to work.  (no biggie, just a quirk)

The shares are served by Ubuntu Server 10.04 64bit and reside in the /srv/samba tree there with each share a separate folder in that tree.  (i.e. /srv/samba/share-name)

Any ideas?[/FONT]

---

### Post by sikander3786 on 2011-02-18
I hope this one will help you.

[http://ubuntu4beginners.blogspot.com/2011/01/how-to-mount-windows-shares-permanently.html](http://ubuntu4beginners.blogspot.com/2011/01/how-to-mount-windows-shares-permanently.html)

---

### Post by EarlsFurniture on 2011-02-25
Thanks, that what I used to use but I had permission issues.

I'll try it again.

I thought cifs was depricated.  That's why I switched it to smbfs.

Or do I not understand something correctly?

I noticed that article was posted 1/25/11 which is pretty new.  But the Ubuntu Wiki says to use smbfs instead.  hmmm....

---

### Post by EarlsFurniture on 2011-02-25
Thanks, [sikander3786]("http://ubuntuforums.org/member.php?u=806649") it looks like this worked.  No permissions issue so far.  Not sure why I had trouble before.

---

