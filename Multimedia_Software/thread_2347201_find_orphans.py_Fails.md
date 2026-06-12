---
title: "find_orphans.py Fails"
date: 2016-12-22
forum: Multimedia Software
---

### Post by jamoody on 2016-12-22
I'm running Mythbuntu 14.04.4 and am trying to cleanup orphaned database entries (entries with missing files).  find_orphans.py has worked well in the past for this but fails on 14.04.4 with an error.  (See [https://forum.mythtv.org/viewtopic.php?f=36&t=1716](https://forum.mythtv.org/viewtopic.php?f=36&t=1716) for history on this problem and the find_orphans.py error traceback.)  The find_orphans failure seems to be caused by bookmarkupdate field being 0000-00-00 00:00:00, reportedly due to mysql being overly aggressive with field checking.  MythTV Support has pointed me to [https://code.mythtv.org/trac/ticket/12871](https://code.mythtv.org/trac/ticket/12871) which contains a patch to make mysql more lenient, but I can't find the location of MythTV.pm in order to make the patch.  

Can anyone point me to where MythTV.pm is located in Mythbuntu 14.04.4?  Does anyone have a better suggestion on how to make mysql more lenient in field checking so it doesn't object when bookmarkupdate field is 0000-00-00 00:00:00?  Thanks.

---

### Post by jamoody on 2016-12-22
Since find_orphans.py is python the suggested update to MythTV.pm doesn't apply.  However I did update /etc/mysql/conf.d/mythtv.cnf to add ALLOW_INVALID_DATES:
[mysqld]
#bind-address=::
max_connections=100
sql_mode="ALLOW_INVALID_DATES"

But after reboot I still get the same problem:

```
Traceback (most recent call last):
  File "./find_orphans.py", line 230, in <module>
    main()
  File "./find_orphans.py", line 214, in main
    opt[1](opt[2])
  File "./find_orphans.py", line 129, in delete_recs
    rec.delete(True, True)
  File "/usr/lib/python2.7/dist-packages/MythTV/dataheap.py", line 365, in delete
    return self.getProgram().delete(force, rerecord)
  File "/usr/lib/python2.7/dist-packages/MythTV/dataheap.py", line 377, in getProgram
    return Program.fromRecorded(self)
  File "/usr/lib/python2.7/dist-packages/MythTV/mythproto.py", line 943, in fromRecorded
    return be.getRecording(rec.chanid, rec.starttime)
  File "/usr/lib/python2.7/dist-packages/MythTV/mythproto.py", line 644, in getRecording
    return Program(res[1:], db=self.db)
  File "/usr/lib/python2.7/dist-packages/MythTV/mythproto.py", line 872, in __init__
    DictData.__init__(self, raw)
  File "/usr/lib/python2.7/dist-packages/MythTV/altdict.py", line 147, in __init__
    data = self._process(data)
  File "/usr/lib/python2.7/dist-packages/MythTV/altdict.py", line 163, in _process
    data[i] = self._trans[self._field_type[i]](v)
  File "/usr/lib/python2.7/dist-packages/MythTV/altdict.py", line 103, in <lambda>
    lambda x: datetime.fromtimestamp(x, datetime.UTCTZ())\
  File "/usr/lib/python2.7/dist-packages/MythTV/utility/dt.py", line 304, in fromtimestamp
    obj = super(datetime, cls).fromtimestamp(float(timestamp), tz)
ValueError: timestamp out of range for platform time_t
```

---

