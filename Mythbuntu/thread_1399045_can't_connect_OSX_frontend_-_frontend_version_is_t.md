---
title: "can't connect OSX frontend - frontend version is too old?"
date: 2010-02-05
forum: Mythbuntu
---

### Post by stib on 2010-02-05
I've downloaded the OSX port of mythfrontend, but if I start it I get this error: ```
"The schema version of your existing database is newer than this version of MythTV understands. Please ensure that you have selected the proper database server or upgrade this and all other frontends and backends to the same MythTV version and revision."
```
I'm guessing that means that the OSX port is too old for the current version of Mythbuntu I have running on my backend (not too sure what version is, but I only just installed it so it's current). Is there a workaround? Can I compile mythfrontend for OSX using a newer version?
Thanks

---

### Post by ian dobson on 2010-02-05
Hi,

If your running Mythbuntu 9.10 then you have a 0.22 version of mythtv (9.04 uses version 0.21).

The error message your seeing is as you've said is that the frontend is older than the backend so they can't communicate with each other.

Have a look here [http://www.mythtv.org/wiki/MythTV_on_Mac_OS_X](http://www.mythtv.org/wiki/MythTV_on_Mac_OS_X) for various builds of the frontend for OSX.

Regards
Ian Dobson

---

### Post by stib on 2010-02-05
Thanks for that. I had actually gone to that page a while ago, but the links were down, so I ended up getting it from somewhere else.

---

