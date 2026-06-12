---
title: "Minidlna segfault"
date: 2014-10-19
forum: Multimedia Software
---

### Post by trasan on 2014-10-19
Hi, 

Have been running minidlna service since some months back and has been working very stable.
Since about a week minidlna crashes very often

dmesg gives:

[39596.172208] minidlna[1684]: segfault at 0 ip 00007f6ceb6fa51c sp 00007fff5e823da8 error 4 in libc-2.15.so[7f6ceb5a4000+1b5000]



Running linux server 
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux



```
dpkg -s minidlna
``` gives
Package: minidlna
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 342
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.0.21+dfsg-1ubuntu1
Depends: libavformat53 (>= 4:0.7-1) | libavformat-extra-53 (>= 4:0.7-1), libavutil51 (>= 4:0.7-1) | libavutil-extra-51 (>= 4:0.7-1), libc6 (>= 2.11), libexif12, libflac8 (>= 1.2.1), libid3tag0 (>= 0.15.1b), libjpeg8 (>= 8c), libogg0 (>= 1.0rc3), libsqlite3-0 (>= 3.5.9), libvorbis0a (>= 1.1.2), adduser (>= 3.11), mawk | gawk
Conffiles:
 /etc/minidlna.conf ced8594e46406725d4ed869de3846930
 /etc/default/minidlna aaf6707ae6b701e19c1c80c7c3999b8e
 /etc/init.d/minidlna 40af0256bcf2e9e4e5451f785a00cdc4





Anybody knows how to fix?

---

