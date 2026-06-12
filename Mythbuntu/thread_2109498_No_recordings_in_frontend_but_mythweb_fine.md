---
title: "No recordings in frontend but mythweb fine"
date: 2013-01-27
forum: Mythbuntu
---

### Post by NathanKell on 2013-01-27
I recently upgraded from 10.04 and 0.24 to 12.04 and 0.25 (now 0.26). A week or so after the upgrade, my recordings don't show in the frontend (I get the "no recordings or still loading" message).
However, they do show up fine in mythweb, and when I go to change filters the numbers are correct (59 crime dramas, for example) but when selected, still, none show up.

The backend log shows nothing strange, but the frontend log shows:
```
Jan 27 18:19:39 mythbox mythlogserver: mythfrontend[2160]: E ProgramInfoLoader remoteutil.cpp:184 (RemoteGetRecordingList) RemoteGetRecordingList() list size appears to be incorrect.
Jan 27 18:19:39 mythbox mythlogserver: mythfrontend[2160]: W CoreContext playbackbox.cpp:1775 (UpdateUILists) PlaybackBox: SortedList is Empty
Jan 27 18:20:38 mythbox mythlogserver: mythfrontend[2160]: W CoreContext playbackbox.cpp:1775 (UpdateUILists) PlaybackBox: SortedList is Empty
```

Program guide still works, you can still watch livetv, and it still seems to be recording and adding shows to the DB (again, visible in mythweb). But nothing under Watch Recordings.

After an exhaustive google, I found this thread that had similar error messages: [http://www.mythtv.dk/viewtopic.php?id=231](http://www.mythtv.dk/viewtopic.php?id=231)
But following the instructions (to remove null characters from the DB) didn't seem to help either.

Any ideas?

---

### Post by dannyboy79 on 2013-01-30
i would suggest going to the mythtv-users IRC channel on freenode, they are very helpful and it's real time support via xchat or whatever IRC chat client you like to use.

---

