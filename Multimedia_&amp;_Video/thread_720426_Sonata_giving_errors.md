---
title: "Sonata giving errors"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by bardic on 2008-03-10
Hey,
I have been trying to get Sonata working all day. I installed mpd and got it work with other clients but I would like to use Sonata since it has a library...

Anyways here's the errors I'm getting...

```

bardic@bardic:~$ sonata
Traceback (most recent call last):
  File "/usr/bin/sonata", line 47, in <module>
    app = sonata.Base()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 590, in __init__
    self.connect(blocking=True)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1624, in connect
    self.connect2(blocking, force_connection)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1636, in connect2
    self.conn = Connection(self)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 146, in __init__
    if not host: host = Base.host[Base.profile_num]
IndexError: list index out of range

```

---

### Post by Hells_Dark on 2008-07-24
Same here.

---

