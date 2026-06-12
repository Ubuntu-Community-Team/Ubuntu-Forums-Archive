---
title: "mount cifs with charset errors"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by nixIT on 2010-11-18
Hello all,

spent some time searching the forums, and saw this question asked, but could not find an answer.

I've been mounting our windows network by opening nautilus and typing in the address bar:

smb://<servername>/share

and I am prompted to log in, all is fine.

however, I need to use some apps where I need to pick the folder from a file list, which I can't get to work with the above connection.

I then created the following line in my fstab file:

```

//<servername>/<share> /mnt/fileserver cifs credentials=/home/<username>/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0

```

This appears to mount correctly, however there are some filenames on the server with the bullet character(•) in their name, and by mounting via fstab, the bullet shows as a question mark, but mounting from nautilus shows the bullet.

Anyway I can mount with fstab, and have all characters show properly in the filename?

--nixIT

---

### Post by matthis on 2011-05-07
Same problem here...

No problem with nautilus, but files with Japanese characters do not appear when mounting with cifs, even when using the iocharset=utf8 option.

The samba server I am connecting to is "Samba 3.0.24-1.35_OSSTECH", on my wzr-hp-g300nh buffalo router. The charset used is CP932.

I have heard that the deprecated smbfs could do this correctly using the codepage option, but it does not seem to work with cifs.

Thank you for any help!

matthis

---

