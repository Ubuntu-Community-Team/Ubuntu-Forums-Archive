---
title: "Mythbuntu Testing PPA Targeting OS Version"
date: 2011-08-10
forum: Mythbuntu
---

### Post by sgunther on 2011-08-10
I recently was tracking down a bug in the MySQL plug-in in MCC and eventually came to the conclusion that the code to validate the connection was incorrect.  I then tracked it down in launchpad and of course it had already been reported and fixed. The issue was in mythbuntu-common mysql.py code and was caused by upgrading the backend from 0.23 to 0.24.  I was curious why if my system was up to date why I had "old" code.  After some more digging it looks as though the mythbuntu codebase is branched by ubuntu release and the 10.04 LTS release is not being kept up with the latest improvements.

An example of mythbuntu-common can be found here;
[https://code.launchpad.net/ubuntu/+source/mythbuntu-common]("https://code.launchpad.net/ubuntu/+source/mythbuntu-common")

If I manually make the changes reflected in the maverick version of mysql.py in mythbuntu-common the MCC MySQL test connection works with a 0.24 backend but the as-delivered version fails.

The mythbuntu team does a great job supporting builds of MythTV for both the latest LTS and latest non-LTS OS versions.

Is there a strategy in place to keep the mythbuntu code in the testing PPA updated and aligned as well?  When I find these type of issues should I create a launchpad bug or is it intended to be this way and LTS releases are limited in testing PPA upgrades?

Respectfully,
-Steve

---

