---
title: "Mythweb error"
date: 2009-10-23
forum: Mythbuntu
---

### Post by xinix on 2009-10-23
I'm getting this error when I try to access mythweb.  I have set the correct permissions.  

Any ideas?

```
Warning: Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php:49) in /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php on line 16
```

---

### Post by jwbrown77 on 2009-10-23
I can't tell you specifically what it is or how to fix it, but I can tell you in PHP you can't call the header() function if any output has already been sent (even whitespace).

So if you had a file like:

<html>
<?php
/* This will give an error. Note the output
 * above, which is before the header() call */
header('Location: [http://www.example.com/');](http://www.example.com/');)
?>

It won't work.

---

### Post by xinix on 2009-10-24
This is with a fresh install of myth and ubuntu 9.04.  The only change I've made was to give the 'www-data' user rights write to the mythweb files.

---

### Post by jwbrown77 on 2009-10-24
Did you update all packages to current?

---

### Post by xinix on 2009-10-24
Yes, everything is updated.

---

### Post by xinix on 2009-10-30
So time has past and new updates have come.

Now I get this error:```
Warning: require(modules/_shared/tmpl/tmpl/header.php) [function.require]: failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23

Fatal error: require() [function.require]: Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
```

It just seems like something didn't install of configure properly.  I have completely removed apache, php, and mythweb including their configs.  After reinstalling, I still get the same thing.

---

### Post by Valen00 on 2009-11-08
take a look at
[https://bugs.launchpad.net/mythbuntu/+bug/459893](https://bugs.launchpad.net/mythbuntu/+bug/459893)

worked for me

---

### Post by xinix on 2009-11-08
I should mark this as resolved.  There is another thread that pointed me in the right way to solving the issue.

---

### Post by joho500 on 2009-11-09
Please supply the link to that thread for future reference.
Thanks.

Cheers,
Joost

---

### Post by xinix on 2009-11-09
> **joho500 said:**
> Please supply the link to that thread for future reference.
Thanks.

[http://ubuntuforums.org/showthread.php?t=1308585](http://ubuntuforums.org/showthread.php?t=1308585)

---

