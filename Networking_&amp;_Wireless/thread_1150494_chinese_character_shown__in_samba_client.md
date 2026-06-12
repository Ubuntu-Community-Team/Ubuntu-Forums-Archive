---
title: "chinese character shown ??? in samba client"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by chaopoch on 2009-05-06
I use samba to connect the Arch linux virtual machine to the Ubuntu host, but all the Chinese character of shared folders are shown ??? in samba client (Arch virtual machine), the charset in /etc/samba/smb.conf is as follows,

unix charset = utf8
display charset = utf8
dos charset = cp950

The locale of Arch linux is en_US.utf8, and the locale of Ubuntu host is zh_TW.utf8, how can I fix the problem?

thanks for reply.

---

