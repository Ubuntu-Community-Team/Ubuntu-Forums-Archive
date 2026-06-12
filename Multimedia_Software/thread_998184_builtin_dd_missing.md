---
title: "builtin_dd missing?"
date: 2008-11-30
forum: Multimedia Software
---

### Post by besson3c on 2008-11-30
Hello,

Since some upgrade (possibly to Ubuntu 8.10) I can no longer use genisoimage/growisofs since builtin_dd is now missing:

> genisoimage -dvd-video -R -J ./mymovie | builtin_dd of=/dev/scd0 obs=32k seek=0
Warning: Disabling Joliet support for DVD-Video.
I: -input-charset not specified, using utf-8 (detected in locale settings)
-bash: builtin_dd: command not found

Why is this, and how do I get builtin_dd back, or do I?

---

### Post by besson3c on 2008-11-30
It actually looks like my genisoimage is completely messed up:

> mkisofs -v -dvd-video -o mymovie.iso ./mymovie
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage 1.1.8 (Linux)
Scanning ./mymovie
Scanning ./mymovie/VIDEO_TS
Segmentation fault

and in /var/log/messages:

> mkisofs[7352] general protection ip:41780c sp:7fffcc8ba960 error:0 in genisoimage[400000+6a000]


These problems may be unrelated, but some sort of upgrade caused these issues... Any suggestions?

---

### Post by tekwiki on 2008-12-15
I'm having the same issue...

---

### Post by besson3c on 2008-12-15
For me the problem was a corrupt DVD structure, this problem is not reproduced with other DVDs.

---

