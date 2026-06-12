---
title: "Mythtv Commercial Flagging"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by Emmo213 on 2007-04-26
I'm currently running 6.10 with the MythTV .20 that's in the repository. Everything was working perfectly
until recently when commercial flagging stopped working. From the backend log I'm seeing this
```
2007-04-21 22:00:02.595 Started recording: The States "California, North Carolina, Kansas, New Hampshire, West Virginia": channel 1056 on cardid 1, sourceid 1
2007-04-21 22:00:18.560 JobQueue: Commercial Flagging Starting for The States "California, North Carolina, Kansas, New Hampshire, West Virginia" recorded from channel 1056 at Sat Apr 21 22:00:00 2007
2007-04-21 22:00:18.953 Using runtime prefix = /usr
2007-04-21 22:00:19.010 New DB connection, total: 1
2007-04-21 22:00:19.025 No program data exists for channel  at
2007-04-21 22:00:19.037 JobQueue: ABORTED Commercial Flagging for The States "California, North Carolina, Kansas, New Hampshire, West Virginia" recorded from channel 1056 at Sat Apr 21 22:00:00 2007.
2007-04-21 23:00:00.952 TVRec(1): Changing from RecordingOnly to None
2007-04-21 23:00:01.091 Finished recording The States "California, North Carolina, Kansas, New Hampshire, West Virginia": channel 1056

```

I'm not sure why it's saying "no program data exists" when it should and then the flagging 
aborts. Has anybody else seen something like this before? Thanks in advance.

---

