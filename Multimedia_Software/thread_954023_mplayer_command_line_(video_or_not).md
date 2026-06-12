---
title: "mplayer command line (video or not)?"
date: 2008-10-20
forum: Multimedia Software
---

### Post by zackiv31 on 2008-10-20
I need a command line call to mplayer, given an input file, that can tell me if the file is a format that mplayer can read.  I've tried something like this:

```
mplayer input.avi -identify -nosound -vo null -nocache -frames 1
```

I then grep that with "Starting playback".. if it finds it, then I know that it can read the file.  If it doesn't, then I know I can't.  This works for video files, and junk files (.txt or whatnot).

My problem is if I input an mp3 into the above command, it proceeds to play it.  How can I adapt the above call so it can handle audio files (and whatever else may be thrown into it).

---

