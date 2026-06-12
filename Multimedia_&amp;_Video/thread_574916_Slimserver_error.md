---
title: "Slimserver error"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by Peregrine88 on 2007-10-13
I installed slimserver the following way:

Added repository, [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main

installed the package:  sudo get-apt update
                                     sudo get-apt slimserver

It seemed to install fine with no errors and then I tried running it like this and got an error:

sudo slimserver
2007-10-13 12:49:30.7118 ERROR: Cannot write to preferences file /home/user/slimserver.pref, any changes made will not be preserved for the next startup of the server

/home/user/Cache/my.cnf: Permission denied at /usr/share/perl5/Slim/Utils/MySQLHelper.pm line 178.
2007-10-13 12:49:30.8761 Use of uninitialized value in sprintf at /usr/share/perl5/Slim/Utils/MySQLHelper.pm line 467.

Any help would be appreciated. :)

---

