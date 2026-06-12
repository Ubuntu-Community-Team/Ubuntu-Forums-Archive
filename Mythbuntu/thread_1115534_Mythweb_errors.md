---
title: "Mythweb errors"
date: 2009-04-03
forum: Mythbuntu
---

### Post by mordoc on 2009-04-03
Folks,

I'm getting the following errors at the top of my listings search page on Mythbuntu:

```
[Error at /usr/share/mythtv/mythweb/modules/tv/includes/objects/Channel.php, line 50:
copy() [function.copy]: The first argument to copy() function cannot be a directory

Error at /usr/share/mythtv/mythweb/modules/tv/includes/objects/Channel.php, line 50:
copy() [function.copy]: The first argument to copy() function cannot be a directory

Error at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:117)
```

Any ideas?  I'm lost on this one...

---

### Post by scweston on 2009-04-28
Hi,

I would like to bump this thread as I'm having a similar issue! If anybody knows how to fix this I would very much appreciate your help.

Thanks in advance.

Stephen

---

### Post by spacedoubtman on 2009-11-09
any luck with this?

I also get a similar error in mythweb:
Warning: Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php:49) in /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php on line 16

This is with a fresh install of ubuntu 9.10 (karmic koala) that I've copied my old mysql database over to.

Edit: I've found other posts that say to try dpkg-reconfigure mythweb, or setting the hostname, but still not working. It looks like the script is working right up until the Modules::getModule call in the headers which seems strange.

---

### Post by ReddogOne on 2009-11-11
Try removing and installing again. Fixed similar problem I had... though why it fixed it... your guess is as good as mine.

EDIT: MythWeb not mythtv

---

