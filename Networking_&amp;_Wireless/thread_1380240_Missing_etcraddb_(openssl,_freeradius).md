---
title: "Missing /etc/raddb/ (openssl, freeradius)"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by HuckBerry on 2010-01-13
Following several of the various freeradius configuration guides, I have notice that they all require the generation of Certs using scripts that (under a standard install) are located in /etc/raddb/certs.

Linux being the way it is, I generally have to go searching for a non-standard directory once or twice per major install. Normally I find what I'm looking for, or find a missing package that needs to be installed but isn't listed as a dependency. 

However I have just about exhausted my filesystem looking for a raddb folder or the ca scripts. I also cannot seem to locate an openssl-dev package (which seems to have some relation to raddb based on what I have read in the forums, something about lisencing) 

Anyone who has successfully configured freeradius with non-cleartext passwords or has any knowledge of raddb, openssl, or Certs is welcome to share their knowledge.
Thanks in advance

---

### Post by changingstate on 2010-01-13
I took a look at the filelist on the ubuntu website : [http://packages.ubuntu.com/karmic/i386/freeradius/filelist](http://packages.ubuntu.com/karmic/i386/freeradius/filelist)

Take a look in /usr/share/doc/freeradius/examples/certs/ for the cert generation files, libssl-dev is what you'll be looking for to build against openssl.

---

### Post by HuckBerry on 2010-01-13
That is an odd place to put a script, generally I don't check the docs for scripts... Why would the Ubuntu mods put that directory in the docs? The readme in that dir still thinks it's in raddb/certs so it wasn't the developers who moved it... odd.

I'll give it a try. Hopefully everything works as planned. Apt says that openssl is installed on my server and I can't find an openssl-dev so hopefully all is well there.

I will report back with any errors, else mark this solved. Thanks a lot!

---

### Post by aatea2010 on 2010-10-28
hello all...

i have got install freeradius + daloradius + mysql IN UBUNTU SERVER LUCID, where i access daloradius and success login, i go management menu and choose List users i have got error message like this :

" Database error
Error Message: DB Error: syntax error
Debug info: SELECT distinct(radcheck,username),radcheck,value, radcheck,id,,groupname as groupname, radcheck,attribute, userinfo,firstname, userinfo,lastname FROM radcheck LEFT JOIN userinfo ON radcheck,username=userinfo,username LEFT JOIN ON radcheck,username=,username WHERE (Attribute LIKE '%-Password') OR (Attribute='Auth-Type') GROUP BY UserName [nativecode=1064 ** You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'groupname as groupname, radcheck,attribute, userinfo,firstname, userinfo,lastnam' at line 2]"

This is my configuration in /var/www/daloradius/mng-list-all.php

$sql = "SELECT distinct(".$configValues['CONFIG_DB_TBL_RADCHECK'].".username),".$configValues['CONFIG_DB_TBL_RADCHEC$
                ".$configValues['CONFIG_DB_TBL_RADCHECK'].".id,".$configValues['CONFIG_DB_TBL_RADUSERGROUP'].".groupname as $
                $configValues['CONFIG_DB_TBL_RADCHECK'].".attribute, ".$configValues['CONFIG_DB_TBL_DALOUSERINFO'].".firstna$
                $configValues['CONFIG_DB_TBL_DALOUSERINFO'].".lastname FROM ".$configValues['CONFIG_DB_TBL_RADCHECK']." ".
                " LEFT JOIN ".$configValues['CONFIG_DB_TBL_DALOUSERINFO']." ON ".
                $configValues['CONFIG_DB_TBL_RADCHECK'].".username=".$configValues['CONFIG_DB_TBL_DALOUSERINFO'].".username $
                " LEFT JOIN ".$configValues['CONFIG_DB_TBL_RADUSERGROUP']." ON ".
                $configValues['CONFIG_DB_TBL_RADCHECK'].".username=".$configValues['CONFIG_DB_TBL_RADUSERGROUP'].".username $
                " WHERE (Attribute LIKE '%-Password') OR (Attribute='Auth-Type') GROUP BY UserName";
        $res = $dbSocket->query($sql);
        $numrows = $res->numRows();

PLEASE SOME ONE HELP ME....
THANK'S

---

