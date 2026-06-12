---
title: "Prefered method to mount Windows shares via the command line"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by mczolton on 2009-08-04
I would like to know, what is the preferred method to mount Windows shares via the command line for Xubuntu 9.04? Has cifs superseded smbfs? 

Thank you!

---

### Post by superprash2003 on 2009-08-04
cifs is i guess better..

---

### Post by mczolton on 2009-08-05
Thank you.

---

### Post by dmizer on 2009-08-05
SMBFS has not been a part of the Ubuntu kernel since Hardy, so yes CIFS. Please see the second link in my sig. If you need smbfs (you shouldn't), then you'll have to compile it yourself.

Of note:
The package "smbfs" still exists, but it is only a metapackage which depends on CIFS and several other samba client related packages. The actual smbfs package is not installed.

---

### Post by slakkie on 2009-08-05
mount -t cifs //path/to/cifs/server/ /path/to/mount/point

---

### Post by mczolton on 2009-08-05
Thank you all very much. This answered my question =)

---

