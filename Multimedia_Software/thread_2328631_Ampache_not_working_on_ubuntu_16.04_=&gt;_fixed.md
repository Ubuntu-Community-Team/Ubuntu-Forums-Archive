---
title: "Ampache not working on ubuntu 16.04 =&gt; fixed"
date: 2016-06-23
forum: Multimedia Software
---

### Post by fionnghall on 2016-06-23
Ampache doesn't seem to support php 7. 

The Ampache Error class conflicts with the builtin Error class of php 7.

## replace all instances of Error with AmpError
# cd /usr/share/ampache/www
# find -type f -name "*.php" -exec grep -HF  "Error::" {} \; | cut -d ':' -f 1 | sort | uniq | xargs sed 's/Error/AmpError/'

## rename the file
# cd /usr/share/ampache/www/lib/class
# mv error.class.php amperror.class.php


See also:
[https://github.com/ampache/ampache/issues/1034](https://github.com/ampache/ampache/issues/1034)

---

