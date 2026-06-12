---
title: "What happens if I start watching a show while it is auto-transcoding?"
date: 2008-01-28
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-01-28
It occurred to me last night.  A show had just finished recording and I was going to watch it, then I wondered what would happen if the auto-transcoding finished while I was watching. I was concerned because the transcode deletes the first file when it completes.

Either the player would crash, or the file would fail to be deleted. In the latter case, transcode would not be able to complete properly.  What does it do in that situation - does it leave large temporary files scattered about?

So, should I avoid watching shows that have just finished recording?

---

### Post by BobLobLaw on 2008-01-29
This has happened to me before, It just kicks you out of the program you are watching.  By the time you re-start the show, the file rename/delete has occured.

---

### Post by stdPikachu on 2008-01-29
Is this true? (Not tried it myself, rarely transcode anything)

UNIX file locking says that if the file doesn't actually get deleted until every process using it has released its handles on it (only the inode pointing at that chunk of data is deleted); you can typically play an MP3 or a video even if you deleted it halfway through. Does Myth break this logic?

---

