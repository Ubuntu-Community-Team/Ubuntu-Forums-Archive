---
title: "aria2 rpc download error"
date: 2012-12-09
forum: Mobile Technology Discussions (CLOSED)
---

### Post by ankushkale1 on 2012-12-09
hi, aria2 made my rooted android mobile a massive download machine.
So i no longer require to keep laptop on. **I am running aria2 as demon on mobile & adding urls from xml-rpc web insterface "webui-aria2" but even i specified in settings that retry download, on error it always stop on minor error & i can't again resume download ( so i stop aria demon by python script (as there is no option in "webui-aria2" interface & again start aria2 demon, this resumes download )**
========================================================================
here is my aria.conf

continue=true
dir=/sdcard/wgeted
max-connection-per-server=5 
file-allocation=none 
min-split-size=1M 
split=5 
max-concurrent-downloads=2 
auto-save-interval=5 
max-tries=0 
save-session=/sdcard/wgeted/aria2.session  
log-level = error
log /sdcard/wgeted/aria2.log
======================================================================
& my aria2 start script

#!/system/bin/sh
downdir=/sdcard/wgeted
downlist=/sdcard/dlist.txt

aria2c --conf-path=/sdcard/dserver/aria.conf --enable-rpc --rpc-listen-all --daemon --input-file $downdir/aria2.session

======================================================================

So plz tell any solution so that even i add url by aria2 web interface it will retry download infinitely if it fails

---

### Post by ankushkale1 on 2012-12-09
well my mobile data connection is not reliable 

so these kind of error i always see

2
If time out occurred.

6
If network problem occurred.

19
If name resolution failed.

common guys any solution?

---

