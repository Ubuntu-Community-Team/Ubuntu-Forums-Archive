---
title: "Recordmydesktop file size limit?"
date: 2010-04-21
forum: Multimedia Software
---

### Post by DodgeV83 on 2010-04-21
Does Recordmydesktop have a file size limit?  I'm considering using the Zero compression setting to keep CPU usage down, but I don't want to run up against a 2GB or 4GB file size limit.  While I know some filesystems impose this limit, most screen recorders I've used have a 2GB or 4GB limit when recording, regardless of the filesystem.  Is this an issue with Recordmydesktop? 

Thanks

---

### Post by DodgeV83 on 2010-04-21
Answered my own question.

Recordmydesktop creates a new img.out video temp file every 500MB, then combines them all at the end.  No crashing involved.

**Stats for those of you who are interested:**

> CPU Usage: 0-1%
File size growth rate with static screen: 0.5MB per second / 30MB per minute

File size growth rate while moving a window around rapidly: 5MB per second / 300MB per minute

**Stats with both Zero Compression and encode-on-the-fly unchecked:**

> CPU Usage: 2%

File size growth rate with static screen: 0.1MB per second / 6MB per minute

File size growth rate while moving a window around rapidly: 1MB per second / 60MB per minute

**Stats with encode-on-the-fly checked at 40 Video quality and 0 Audio Quality (64k bitrate Ogg audio):**

> CPU Usage: 12%
File size growth rate with static screen: .025MB (25kb) per second / 1.5MB per minute

File size growth rate while moving a window around rapidly: 0.1MB per second / 6MB per minute

---

