---
title: "Prob starting Openshot 1.4"
date: 2012-02-08
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2012-02-08
Hi all,

Having installed and downloaded the latest Openshot 1.4.2 video editor, I find it won't launch at all. When you click the icon, it pulsates but then does nothing.

When run in Terminal, I get this:
```
baldrick@baldrick-8gig:~$ openshot

------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------

** WARNING **: Trying to register gtype 'GMountMountFlags' as enum when in fact it is of type 'GFlags'

** WARNING **: Trying to register gtype 'GDriveStartFlags' as enum when in fact it is of type 'GFlags'
--------------------------------
   OpenShot (version 1.4.2)
--------------------------------
Process no longer exists: 3635.  Creating new pid lock file.
mlt_repository_init: failed to dlopen /usr/lib/mlt/libmltavformat.so
  (/usr/lib/mlt/libmltavformat.so: symbol ff_cropTbl, version LIBAVCODEC_53 not defined in file libavcodec.so.53 with link time reference)

Detecting formats, codecs, and filters...
Segmentation fault (core dumped)
baldrick@baldrick-8gig:~$ 

```

It's got me beat. Can anyone please help to resolve the above issues?

Cheers.

---

### Post by Chris Giltnane on 2012-02-09
No answers for you, I have got exactly the same problem.

---

### Post by labinnsw on 2012-04-25
Bump

---

