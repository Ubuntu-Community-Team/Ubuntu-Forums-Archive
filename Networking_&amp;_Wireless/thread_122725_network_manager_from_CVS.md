---
title: "network manager from CVS"
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by jeremytaylor on 2006-01-28
Hi there, 
I've been having problems with Network manager from the repositories so thought I might try the CVS version. However I can't install it! 

this seems to be where it finally gets to in the autogen script 

checking for LIBNL... configure: error: Package requirements (libnl-1) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

but earlier i get messages 

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

which might also be the problem
I've tried install libnl and it seemed to work but it made no difference. 

Any suggestions?
Jeremy

---

