---
title: "CIFS &amp; copying large files"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by Xyphoid on 2009-04-24
I just installed Ubuntu 9.04 on my Acer Aspire One.
I installed smbf and mounted an XP shared network folder in my fstab:

//192.168.1.100/Data /home/user/Data cifs credentials=/root/.smbcredentials,iocharset=utf8,auto 0 0

Connected with wifi I can browse the folder and copy small files. But if I try to copy files larger than 500 MB, the file transfer hangs after a couple hunderds MB's. This also happens if I mount the folder manually.

My dmesg says:

[ 1475.113383] ath5k phy0: unsupported jumbo
[ 1496.117132]  CIFS VFS: server not responding
[ 1496.117154]  CIFS VFS: No response to cmd 46 mid 1449
[ 1496.117171]  CIFS VFS: Send error in read = -11
[ 1556.116170]  CIFS VFS: Unexpected lookup error -112

In Jaunty Beta it worked. If I use **Places/Network** it also hangs when copying large files.
If I connect with wire, the file transfer works normal. 
Does anybody have a solution?

---

### Post by Xyphoid on 2009-04-24
I found the cause of the problem.
I already tried the madwifi driver under **System/Administration/Hardware Drivers** but that didn't work either.
So I installed the madwifi driver using [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Now I can copy large files with CIFS again.
It took me all night and all day to get to that solution...But I am happy!!!! :p :popcorn: :guitar: :-({|= :grin: =D>:-\"\\:D/

---

