---
title: "tcpdump will not work"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by jabeavers on 2010-08-24
I have a fairly new install of xubuntu. I needed to use tcpdump and it is not working. This is the error it gives me:

tcpdump: error while loading shared libraries: libpcap.so.0.8: cannot open shared object file: No such file or directory

I have uninstalled and reinstalled tcpdump and libpcap0.8 several times and I get the same error every time I try to use this.

Here's a pertinent line from sudo strace tcpdump:
open("/usr/lib/libpcap.so.0.8", O_RDONLY) = -1 EACCES (Permission denied)

ls -l /usr/lib/libpcap*
lrwxrwxrwx 1 root root     16 2010-08-24 14:29 /usr/lib/libpcap.so.0.8 -> libpcap.so.1.0.0
-rw-r--r-- 1 root root 204128 2010-01-04 19:15 /usr/lib/libpcap.so.1.0.0

Thanks,
John

---

