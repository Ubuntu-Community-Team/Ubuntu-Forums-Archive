---
title: "Delete recordings with missing files"
date: 2014-09-29
forum: Mythbuntu
---

### Post by lordviperz on 2014-09-29
I recently had a corrupt file system that resulted is the loss of a dozen files of recordings. I was not able to recover them but that isn't my problem now. The problem now is these recordings are still listed in the recordings and show a X in a circle for the missing file. When I go to delete these recordings they move over to the, I don't remember what it is called, trash where they stay for a short while in case you want to recover them. Now they never get removed from there and I assume it's because they have no actual file to delete. Is there a way to clear them out?

---

### Post by lordviperz on 2014-09-29
Here is some info from the backend log when I try to delete a recording with a missing file.

Sep 29 11:13:45 MythTV-2 mythbackend: mythbackend[2751]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Sep 29 11:13:45 MythTV-2 mythbackend: mythbackend[2751]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: MythTV-2 as a client (events: 0)
Sep 29 11:13:45 MythTV-2 mythbackend: mythbackend[2751]: E ProcessRequest programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(6044_20140925020000.mpg): GetPlaybackURL: '6044_20140925020000.mpg' should be local, but it can not be found.
Sep 29 11:13:45 MythTV-2 mythbackend: mythbackend[2751]: E ProcessRequest mainserver.cpp:2695 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/MythTV-2/6044_20140925020000.mpg. File doesn't exist.  Database metadata will not be removed.

---

### Post by khPWXxF on 2014-09-29
The utility find_orphans.py is designed for this.  It's probably on your system already - find it with
```
locate find_orphans.py
```

Then run it with
```
/where/it/is/find_orphans.py
```
Phil

---

### Post by lordviperz on 2014-09-29
> **khPWXxF said:**
> The utility find_orphans.py is designed for this.  It's probably on your system already - find it with
```
locate find_orphans.py
```

Then run it with
```
/where/it/is/find_orphans.py
```
Phil

Thanks for this. I also just discovered if I manually create the missing file using touch, then the system will auto-expire the recording since it now has a file to delete. But I'll use the orphans script so I don't have to manually create so many files.

Now I'm off to see if I can figure out why I lost all those files in the first place.

---

