---
title: "Find_Orphans script"
date: 2014-09-09
forum: Mythbuntu
---

### Post by drifting on 2014-09-09
Anyone have an idea why I am getting this error? was trying to have a clean up prior to trying the upgrade to 14.04. Currently on 12.04 and .27 Myth

paul@MicroServer:~$ ./find_orphans.py 
Traceback (most recent call last):
  File "./find_orphans.py", line 222, in <module>
    BE = MythBE(db=DB)
  File "/usr/lib/python2.7/dist-packages/MythTV/mythproto.py", line 93, in __init__
    self.port = int(self.db.settings[self.hostname].BackendServerPort)
TypeError: int() argument must be a string or a number, not 'NoneType'

---

### Post by ian-weisser on 2014-09-10
Please file a bug report for the error. It seems like a fairly easy fix.

---

