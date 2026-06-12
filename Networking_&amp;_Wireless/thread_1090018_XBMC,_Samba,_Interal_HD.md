---
title: "XBMC, Samba, Interal HD"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by puner on 2009-03-07
Hello

I have two HD's in my computer with ubuntu one one IDE and my media files on a SATA drive.

I want to share my SATA drive so I can see my media on my xbox. I noticed that when I right click on the drive there is no option to share, so what I decided to share was the individual folders (music, pictures, videos) inside the drive.

For example when I chose to share "My Videos" I got the errro:

```
'net usershare' returned error 255: net usershare add: cannot share path /media/Entertainment/My Videos as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.
```

I added the link to the smb.conf file but it did nothing.

---

