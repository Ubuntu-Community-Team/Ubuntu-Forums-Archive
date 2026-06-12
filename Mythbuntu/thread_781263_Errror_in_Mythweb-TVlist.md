---
title: "Errror in Mythweb-TVlist"
date: 2008-05-04
forum: Mythbuntu
---

### Post by RWN on 2008-05-04
The last Day´s I get this Error

```
Fatal error: Allowed memory size of 33554432 bytes exhausted (tried to allocate 71 bytes) in /usr/share/mythtv/mythweb/modules/tv/includes/objects/Program.php on line 291
```

What can I do ?

---

### Post by ian dobson on 2008-05-04
Hi,

php is running out of memory. You can try increasing it by editing apache.conf (or /etc/apache2/sites-enabled/mythweb.conf) and adding/editing the line:-

php_value memory_limit                  32M

32Mb is the default value, maybe try 48M.
I'm not sure exactly which file needs to be edited but it must be in the /etc/apache2/ directory or one of the subdirectories.

Regards
Ian Dobson

---

### Post by karlec on 2008-05-04
You need to change the settings in mythweb.conf:
/etc/apache2/sites-available/mythweb.conf

Change the following line to a higher value:
php_value memory_limit 32M


I had to change mine to 250M in order to get the canned searches and the listing to work.

Hopefully that helps.

Cheers

---

### Post by SgtDude on 2008-09-09
Thanks guys.  I had exactly the same problem, and this fixed it quickly and effortlessly.

---

### Post by damirabal on 2008-12-01
> **karlec said:**
> You need to change the settings in mythweb.conf:
/etc/apache2/sites-available/mythweb.conf

Change the following line to a higher value:
php_value memory_limit 32M


I had to change mine to 250M in order to get the canned searches and the listing to work.

Hopefully that helps.

Cheers

I used 256M ans still the canned searches fail. I'll try increasing it tonight.

Dennis

---

