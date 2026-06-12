---
title: "VLC right-click 'add to playlist' functionality?"
date: 2009-03-07
forum: Multimedia Software
---

### Post by Pipps on 2009-03-07
I use VLC for all audio and video files. 

When playing audio, I would find it very useful to be able to browse through my file folders and add further items to the VLC playlist by simply right-clicking on them in turn, rather than having to drag them to the VLC playlist window.

Would it be possible to use a script to provide this right-click functionality?

I am sure that a lot of VLC users would find it very useful!

---

### Post by mc4man on 2009-03-07
Unfortunately vlc doesn't offer any commands for "append' or 'enqueue'
At some point if the 'only use 1 instance' and the 'enqueue files when in 1 instance' could work at the same time then it would be possible

Amarok and audacious are very well suited in this regard (controlling files and folders from right click. ( both have the equivalent of 'load', 'append', and 'enqueue', any of which can be paired with 'play' 
Generally the play is best paired with load

---

### Post by craptree on 2010-03-06
You can with the following command

```
vlc --started-from-file --playlist-enqueue
```

---

