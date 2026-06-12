---
title: "NDAS &quot;Stale NFS file handle&quot;"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by narodo on 2009-08-23
Hi guys,

I hope you can help me out with this.

I have a Ximeta NDAS Netdisk running but I get the following message for some folders:
cd: xxx: Stale NFS file handle

If I do a "ls -l" I get the following for some folders:
d?????????  ? ?    ?          ?                ? temp
d?????????  ? ?    ?          ?                ? temp_1

I already unmounted and remounted the disk.
I also tried to mount it to a fresh mount point.
But to no avail.

It's quite frustrating since the folders in questions contain some of my personal fotos and I would hate to lose them.

Any suggestions are highly appreciated!

Thanks for your help!

PS: this is my first post... hope I didn't violate any rules and put the thread in the right category :)

---

### Post by narodo on 2009-08-30
Just in case somebody else runs into this...

Turns out the file system was messed up.
I ran fcsk and it corrected  tons of errors. 

The folders are accessible again and I think all files (as far as I could see) were recovered.
Happy days!

---

