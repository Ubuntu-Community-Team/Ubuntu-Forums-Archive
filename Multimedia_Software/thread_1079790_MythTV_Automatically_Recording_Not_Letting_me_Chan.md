---
title: "MythTV Automatically Recording Not Letting me Change Channel"
date: 2009-02-24
forum: Multimedia Software
---

### Post by mastermindg on 2009-02-24
I've setup MythTV and the channels are set and everthing seems to be working ok, but I am not able to change the channel. If I hit the up/down button it does nothing, when I look at mythbackend.log it is showing:

```
2009-02-24 19:12:02.612 New DB connection, total: 1
2009-02-24 19:12:02.628 Connected to database 'mythconverg' at host: localhost
2009-02-24 19:12:02.631 Closing DB connection named 'DBManager0'
2009-02-24 19:12:02.633 Connected to database 'mythconverg' at host: localhost
2009-02-24 19:12:02.636 New DB connection, total: 2
2009-02-24 19:12:02.643 Connected to database 'mythconverg' at host: localhost
2009-02-24 19:12:02.648 Current Schema Version: 1214
2009-02-24 19:12:02.668 Preview Error: Previewer file '/home/ken/.mythtv/live/1021_20090224191159.mpg' is not valid.
2009-02-24 19:12:02.677 Preview Error: Run() file not local: '/home/ken/.mythtv/live/1021_20090224191159.mpg'
2009-02-24 19:12:02.688 Preview Error: Preview process not ok.
			fileinfo(/home/ken/.mythtv/live/1021_20090224191159.mpg.png) exists: 0 readable: 0 size: 0
2009-02-24 19:12:40.809 TVRec(1): Changing from WatchingLiveTV to None
2009-02-24 19:12:40.900 Finished recording Greater Boston: channel 1021
2009-02-24 19:14:08.564 Expiring 0 MBytes for 1021 @ Tue Feb 24 19:00:00 2009 => Greater Boston
```

How can I get it to stop recording instantly and allow me to just watch TV?

---

