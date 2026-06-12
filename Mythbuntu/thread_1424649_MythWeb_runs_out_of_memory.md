---
title: "MythWeb runs out of memory"
date: 2010-03-08
forum: Mythbuntu
---

### Post by dsbw on 2010-03-08
So, I'm getting the dreaded: 

```
"Fatal error: Allowed memory size of 33554432 bytes exhausted (tried to allocate 51 bytes) in /usr/share/mythtv/mythweb/includes/translate.php on line 142"

```

on most pages of MythWeb. I have gotten this error for a long time and I know the solution is supposed to be to change the memory limit in PHP.INI.

This has never, ever worked for me. First of all, my PHP.INI (which I reset on last upgrade) isn't set to 32M as shown above, it's set to 16M. (Setting to 16M is listed as the fix in most cases. Heh.)

Second, and not surprisingly, it doesn't matter WHAT I set the memory limit to, it doesn't change the 33554432 error message.

I have only one PHP.INI file on my drive. /etc/php5/apache2

Used to have two, but changing either didn't have any noticeable effect. So, there's gotta be another config file, right?

---

### Post by pu15e on 2010-03-08
Tried /etc/apache2/sites-available/mythweb.conf ?

You don't say what version you're running, but mine (Karmic, up to date as of today including -fixes) shows the directive you're looking for at line 118 of that file ;-)

Cheers,
 Mattt.

---

### Post by dsbw on 2010-03-13
I'll be damned. There it is and it worked. Figured it had to be something like that. 

Thanks much.

---

