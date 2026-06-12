---
title: "Mythweather source setting for UK"
date: 2010-01-26
forum: Mythbuntu
---

### Post by rosbif on 2010-01-26
I'm running 0.22 on Ubuntu 9.10.  I've got Mythweather running, but it doesn't seem to have a setup option for selecting the BBC weather sources - whenever I search for a location, it uses the ENVCAN or NDFD sources.  I can see an entry for BBC current and 3-day sources in the DB and the scripts seem to be in place. Help!

---

### Post by My Name on 2010-03-08
did anyone get to the bottom of this as I'm am stumped.
You'd think that London, England would be a valid location...

---

### Post by scotta228 on 2010-04-29
This patch did it for me:

[http://svn.mythtv.org/trac/attachment/ticket/7758/7758.diff](http://svn.mythtv.org/trac/attachment/ticket/7758/7758.diff)

The bbc website has been changed, so the location search base URL and parameters have changed.

---

