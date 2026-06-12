---
title: "No sound on remote machine when tunneling X over SSH"
date: 2011-08-07
forum: Multimedia Software
---

### Post by pyraz on 2011-08-07
I just upgraded my MediaCenter to Ubuntu 11.04, apparently this was a mistake. I used to play music off it by doing the following
```
ssh -X me@mymediacenter
```
Then running
```
rhythmbox-client
```

Rhythmbox would appear on my local screen, but the sound would come out of my MediaCenter, perfect!

Now, however, after the upgrade, I can ssh in just fine, launch Rhythmbox just fine, but no sound. If I VNC in, and launch Rhythmbox locally, it plays sound just fine. But over SSH, no cigar. What changed? I don't remember having to do anything special to make this work before. Any suggestions?

---

