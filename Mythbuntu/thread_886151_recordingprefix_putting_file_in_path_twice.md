---
title: "recordingprefix putting file in path twice?"
date: 2008-08-10
forum: Mythbuntu
---

### Post by MonkeyKnifeFight on 2008-08-10
I want to use mytharchive on my frontend system so I add RecordFilePrefix to the DB. But now I can't watch recordings, nor can I burn dvds through mytharchive. It complains that the file is not available. Checking the frontend logs I see this...

```
2008-08-10 09:11:48.688 PlaybackBox::play(): Error, /mnt/tv/1271_20080809182700.mpg/1271_20080809182700.mpg file not found
2008-08-10 09:11:48.699 Connecting to backend server: 10.0.0.5:6543 (try 1 of 5)
2008-08-10 09:11:48.700 Unable to find image file: /mnt/tv/1271_20080809182700.mpg/1271_20080809182700.mpg.png
```

So why is it putting the video in the path twice? I really want to archive some stuff to make room for the Olympics.

Got any ideas?

---

### Post by MonkeyKnifeFight on 2008-08-11
Hmmm... so I got it working, but I'm not really sure how. While I was poking around the DB I saw the storagegroups table and thought maybe I should add a record for the frontend. So I did and it seemed to work.

I noticed some errors about trying to find the backend process, I figured I must have confused the frontend to think it was the backend. So I flipped the record back, but the fix seemed to hold. I don't know what happened but it's finding the files and mytharchive seems to work.

---

