---
title: "Suddenly can't connect to mythweb"
date: 2014-09-23
forum: Mythbuntu
---

### Post by mma8x on 2014-09-23
Running Kubuntu 14.04, and stock versions of mythtv/mythweb.  I didn't think that I'd changed anything in my config, or updated anything (maybe I updated something though), but started getting some sort of 404 error when trying to connect to [http://myhost/mythweb](http://myhost/mythweb).  Uninstalled/reinstalled mythweb, and now end up with the following error when I try to connect:

```
Fatal Error

!!NoTrans: Access denied for user 'mythtv'@'MythBox.local' (using password: YES) [#1045]

Backtrace
Array
(
[0] => Array
(
[file] => /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
[line] => 63
[function] => error
[class] => Database
[object] => Database_mysql Object
(
[dbh] => 
[error] => Access denied for user 'mythtv'@'MythBox.local' (using password: YES) [#1045]
[err] => Access denied for user 'mythtv'@'MythBox.local' (using password: YES)
[errno] => 1045
[last_sh] => Database_Query_mysql Object
(
[dbh] => 
[query] => Array
(
[0] => SET NAMES utf8;
)

[last_query] => SET NAMES utf8;
[warnings] => Array
(
)

[num_args_needed] => 0
[num_rows] => 
[affected_rows] => 
[insert_id] => 
[db] => Database_mysql Object
*RECURSION*
)

[fatal_errors] => 1
[query_count] => 0
[query_time] => 0
[global_name] => 
[destruct_handlers] => Array
(
)

)

[type] => ->
[args] => Array
(
)

)

[1] => Array
(
[file] => /usr/share/mythtv/mythweb/classes/Database.php
[line] => 261
[function] => execute
[class] => Database_Query_mysql
[object] => Database_Query_mysql Object
(
[dbh] => 
[query] => Array
(
[0] => SET NAMES utf8;
)

[last_query] => SET NAMES utf8;
[warnings] => Array
(
)

[num_args_needed] => 0
[num_rows] => 
[affected_rows] => 
[insert_id] => 
[db] => Database_mysql Object
(
[dbh] => 
[error] => Access denied for user 'mythtv'@'MythBox.local' (using password: YES) [#1045]
[err] => Access denied for user 'mythtv'@'MythBox.local' (using password: YES)
[errno] => 1045
[last_sh] => Database_Query_mysql Object
*RECURSION*
[fatal_errors] => 1
[query_count] => 0
[query_time] => 0
[global_name] => 
[destruct_handlers] => Array
(
)

)

)

[type] => ->
[args] => Array
(
[0] => Array
(
)

)

)

[2] => Array
(
[file] => /usr/share/mythtv/mythweb/classes/Database.php
[line] => 124
[function] => query
[class] => Database
[object] => Database_mysql Object
(
[dbh] => 
[error] => Access denied for user 'mythtv'@'MythBox.local' (using password: YES) [#1045]
[err] => Access denied for user 'mythtv'@'MythBox.local' (using password: YES)
[errno] => 1045
[last_sh] => Database_Query_mysql Object
(
[dbh] => 
[query] => Array
(
[0] => SET NAMES utf8;
)

[last_query] => SET NAMES utf8;
[warnings] => Array
(
)

[num_args_needed] => 0
[num_rows] => 
[affected_rows] => 
[insert_id] => 
[db] => Database_mysql Object
*RECURSION*
)

[fatal_errors] => 1
[query_count] => 0
[query_time] => 0
[global_name] => 
[destruct_handlers] => Array
(
)

)

[type] => ->
[args] => Array
(
[0] => SET NAMES utf8;
)

)

[3] => Array
(
[file] => /usr/share/mythtv/mythweb/includes/database.php
[line] => 49
[function] => connect
[class] => Database
[type] => ::
[args] => Array
(
[0] => mythconverg
[1] => mythtv
[2] => *mydbpw*
[3] => 192.168.1.4
[4] => 
[5] => mysql
)

)

[4] => Array
(
[file] => /usr/share/mythtv/mythweb/includes/init.php
[line] => 43
[args] => Array
(
[0] => /usr/share/mythtv/mythweb/includes/database.php
)

[function] => require_once
)

[5] => Array
(
[file] => /usr/share/mythtv/mythweb/mythweb.php
[line] => 20
[args] => Array
(
[0] => /usr/share/mythtv/mythweb/includes/init.php
)

[function] => require_once
)

)
!!

If you choose to submit a bug report please make sure to include a brief description of what you were doing, along with the following backtrace as an attachment (please don\'t just paste the whole thing into the ticket)


```

I'm thinking it can't connect to mysql for some reason, but not sure why.  Guessing there's a config file somewhere with a password or network address set wrong... Everything else is working fine, I have the backend serving remote machines on my LAN without an issue.

---

### Post by Adam_Jacobs on 2014-09-23
I had a very similar problem, and it was indeed a failure to connect to the MySQL database.

In my case, it was solved by editing the Apache config file for Mythweb, which I found at /etc/apache2/sites-available/mythweb.conf

The file should have all the details for connecting to the database, and if they're wrong, I believe that causes the error you're getting.

---

### Post by mma8x on 2014-09-23
Yup, that was exactly the problem.  I had already looked through that file but must have missed it.  For some reason the password in that file was set to my system username pw instead of the mysql pw.  Weird, since it shouldn't have ever been able to connect like that.  Thanks for the help.

---

### Post by mma8x on 2014-11-15
> **mma8x said:**
> Yup, that was exactly the problem.  I had already looked through that file but must have missed it.  For some reason the password in that file was set to my system username pw instead of the mysql pw.  Weird, since it shouldn't have ever been able to connect like that.  Thanks for the help.

Strange, this happened again after a system upgrade.  Remembered having this problem a while ago, and forgot how I fixed it.  Thanks again!

---

