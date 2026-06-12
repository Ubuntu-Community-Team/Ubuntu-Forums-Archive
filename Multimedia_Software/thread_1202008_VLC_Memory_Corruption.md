---
title: "VLC Memory Corruption"
date: 2009-07-01
forum: Multimedia Software
---

### Post by Cyclops_ on 2009-07-01
Hey, all,

I am having a problem with VLC.  It was working a couple of days ago, and I am not sure what I did to kill it.

It just plain won't open.  I can't right click a file and do Open With..., or open it directly, or anything.

So I removed it completely (including configuration files) and reinstalled.  Twice.

I also deleted my .vlc folder.

When I run from the command line, the following kinda sticks out to me:

```

[00000001] main libvlc debug: translation test: code is "C"
*** glibc detected *** vlc: malloc(): memory corruption: 0x087907f8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7dca276]
/lib/tls/i686/cmov/libc.so.6(__libc_calloc+0xef)[0xb7dcb6ef]
/usr/lib/libvlccore.so.0[0xb7f71a4f]

```Any help would be Awesome!

---

### Post by Cyclops_ on 2009-07-03
... Bump

---

### Post by Cyclops_ on 2009-07-03
This is version 0.9.9a, and it happened right after I tried to add some French streaming channel thing.  I wish I knew the site I was getting the info from so I could post it.

Can anyone help?

Thanks much if you can :)

---

### Post by mc4man on 2009-07-03
Start vlc like this and see what happens, post output if needed

 ```
vlc --reset-config --reset-plugins-cache -vv
```

---

### Post by Cyclops_ on 2009-07-04
Oh, AWESOME!  I have my VLC Back!!


THANK YOU! :)

---

