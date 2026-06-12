---
title: "MythWeb broken - Failed to set php timezone to EDT"
date: 2010-09-23
forum: Multimedia Software
---

### Post by Taylorcraft078 on 2010-09-23
I let the machine update the other night.  Now MythWeb is broken with these lines appearing either at the top of the listings or as the only thing on the page.

[INDENT]User Notice at /usr/share/mythtv/mythweb/classes/MythBackend.php, line 124:
Failed to set php timezone to EDT Response from backend was Array ( [0] => EDT [1] => -14400 [2] => 2010-09-21T21:27:32 ) 

Warning at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:148)[/INDENT]

Looking at MythTV pages it looks like this got broken in late August but should be fixed by now.

Looking at Synaptic it looks like I am at the current version.

Any suggestions on how to fix it or back it down?

Dave

---

### Post by Taylorcraft078 on 2010-09-27
No hints at all?  I have not upgraded to the latest LTS version yet.  

It looks like the patch introduced some MythTV .23 or .24 change.  I am running MythTV .22.

Will upgrading to the latest LTS version of Ubuntu drag in a newer MythTV?  Will I have to build a Myth from the sources to get back in sync?  There doesn't seem to be an Ubuntu binary for .23.

Dave

---

