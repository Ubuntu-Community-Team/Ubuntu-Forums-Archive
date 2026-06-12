---
title: "Problem with 0.23 backend"
date: 2010-06-06
forum: Mythbuntu
---

### Post by extasy on 2010-06-06
After upgrade to 0.23 I get this error message:

2010-06-06 17:51:16.500 mythbackend version: branches/release-0-23-fixes [24836] [www.mythtv.org](www.mythtv.org)
2010-06-06 17:51:16.562 Using runtime prefix = /usr
2010-06-06 17:51:16.612 Using configuration directory = /.mythtv
2010-06-06 17:51:16.662 Cannot locate your home directory. Please set the environment variable HOME
2010-06-06 17:51:16.712 Failed to init MythContext, exiting.


Any Idea how to solve this?

Kind regards
Henrik

---

### Post by extasy on 2010-06-06
According to #mythtv-users this must be a bug in mythbuntu repros. 

from Sphery: but somehow the Mythbuntu guys need to make sure that mythbackend is executed in an environment with a proper HOME directory specified.  I don't know if they would do that in their wrapper script (don't they still have a mythbackend and mythbackend.real?) or what, but it needs set somewhere.

---

### Post by ehaus on 2010-06-07
I am having the exact same problem.  My mythbackend.log file gives the same message:

mythbackend version: branches/release-0-23-fixes [24710] [www.mythtv.org](www.mythtv.org)
2010-06-07 20:24:45.202 Using runtime prefix = /usr
2010-06-07 20:24:45.203 Using configuration directory = /.mythtv
2010-06-07 20:24:45.204 Cannot locate your home directory. Please set the environment variable HOME
2010-06-07 20:24:45.205 Failed to init MythContext, exiting.

Any news of a fix?

---

### Post by ian dobson on 2010-06-07
Hi,

This message is just stating the the mythtv user that's starting mythbackend doesn't have a home directory defined under /home.

Could you supply a copy of the following files:-
/etc/init/mythtv-backend.conf and
/etc/default/mythtv-backend

and the output from ls -o /home

Regards
Ian Dobson

---

