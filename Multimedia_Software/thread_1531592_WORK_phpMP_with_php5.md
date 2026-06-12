---
title: "WORK: phpMP with php5"
date: 2010-07-15
forum: Multimedia Software
---

### Post by akoch on 2010-07-15
Hi,
 
yesterday i install the first time phpMP and php5 on the same Machine.
 
But phpMP and php5 WORK.
 
Workaround:
 
$HTTP_GET_VARS and $HTTP_POST_VARS doesn´t work with php5

Modify to $_GET and $_POST - and all is fine
 
In this file you must modify:
 
find_body.php
login_body.php
main_body.php
playlist.php
search_body.php
stats_body.php
stream_body.php
update_body.php
 
Greatings
 
Andreas:popcorn:

---

### Post by tswaehn on 2011-09-20
you might also want to check out this

[http://phpmpreloaded.sourceforge.net/](http://phpmpreloaded.sourceforge.net/)

---

