---
title: "samba share cannot access symbolic links to other drives"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by qip on 2011-01-10
I've created two samba shares, /media/disk1 and /media/disk2
say the structure is like this:
/media/disk1/dir1
/media/disk1/dir2 links to /media/disk1/dir1
/media/disk2/dir1 links to /media/disk1/dir1

so I can access /media/disk1/dir1 and /media/disk1/dir2 from samba share, but I cannot access /media/disk2/dir1, on Windows 7 it throws:
> [Window Title]
Location is not available

[Content]
N:\dir1 is not accessible.

Access is denied.


[OK]

In conclusion, symbolic inside the same drive is okay, but when cross-drive links happened, I cannot access them..
Is there anything I have missing or done wrongly? Thanks.

---

### Post by PatchesTheCaveman on 2011-01-10
You need to set
```
follow symlinks = yes
wide links = yes
```
for the share in smb.conf for Samba to follow symlinks out of the file share.

ETA:  You will also need to add:
```
unix extensions = no
```
to your *[global]* sections for security reasons.  For more information, see [http://www.ubuntu.com/usn/usn-918-1](http://www.ubuntu.com/usn/usn-918-1)

---

### Post by qip on 2011-01-10
Thank you!
Previously I did add the three command all into [global] and that is why it didn't work..
Now I add the first 2 lines to each of the shares and it works fine.
Again, thank you for the time:)

---

