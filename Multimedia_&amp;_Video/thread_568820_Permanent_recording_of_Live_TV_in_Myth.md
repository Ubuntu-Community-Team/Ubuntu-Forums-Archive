---
title: "Permanent recording of Live TV in Myth"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by derby007 on 2007-10-06
When I go into watch LiveTV in Myth, I can watch TV (as intended !) BUT....its permanently storing the file to my HD, ie. I thought it was supposed to delete this file, ie. if you are not recording or if no schedule is set ??? any suggestions, as I have thrawled thru all the settings. :confused:

---

### Post by jimbodude21 on 2007-10-06
MythTV will keep the live recording until the space is needed by another recording, or the live recording reaches a certain age.  Look in Information Center --> System Status --> AutoExpire List.  You should see "Live TV" entries in that list.  The list is checked every 10 minutes, and shows near the top are usually automatically marked expired and deleted.

If you find that live tv recordings are hanging around too long, look at the setting under Utilities/Setup --> Setup --> TV Settings --> General, AutoExpire page (it's the second).  There is a setting for "LiveTV recordings Max Age" - I'm not sure what this is measured in, but mine is set to 1, and that seems to work pretty well.  Also make sure that the "Auto Expire Default" is turned on to make sure shows are marked as expirable.

There is also a setting on this page called "Extra Disk Space" to tell MythTV how much of the hard drive it is not allowed to use - adjusting that might free up additional space if you need it.

---

### Post by derby007 on 2007-10-15
Cheers for that, this is working now.

---

