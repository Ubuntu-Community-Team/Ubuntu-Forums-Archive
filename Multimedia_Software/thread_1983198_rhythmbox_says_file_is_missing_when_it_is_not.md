---
title: "rhythmbox says file is missing when it is not"
date: 2012-05-19
forum: Multimedia Software
---

### Post by xiphosurus on 2012-05-19
i use unison to sync all my music bidirectionally computer at work and another at home. i also sync the database and playlist from rhythmbox.

however, the rhythmdb.xml file includes this line <mountpoint>file:///media/xxx</mountpoint> where xx is the name of the hdd the music file is on. at home and work, they are both symbolically linked to different hdds. 

when i do add music to one location and sync it across to the other, rhythmbox adds <mountpoint>file:///media/xxx</mountpoint> for the new file, and when synced and open rhythmbox at the other location, the new song shows up as missing, even though unison has synced it over.

one way to solve this problem is to just manually delete this <mountpoint> line. but i was wondering if anyone here knows if there is a way to prevent rhythmbox from adding this <mountpoint> line in the first place. TIA!

---

