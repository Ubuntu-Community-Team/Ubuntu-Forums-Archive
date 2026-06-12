---
title: "VLC Memory Leak"
date: 2010-05-05
forum: Multimedia Software
---

### Post by moffa on 2010-05-05
As I watch a movie using VLC, after about 20 minutes or so, I"m completely out of memory and my swap file is increasing rapidly. Would someone help me troubleshoot the issue? I've had it since I upgraded to test 10.04 Alpha 2(or around there) x64.

I reset my settings in VLC, there seems to be a problem with Post Processing and Deinterlacing as they were the only two setting I had applied.

---

### Post by tmcmurph on 2011-05-23
I've tried alsa and same thing. RAM gets eaten and swap and system dies. Totem Movie Player works fine as do some other players.

---

### Post by mc4man on 2011-05-23
You could read thru this thread
[http://ubuntuforums.org/showthread.php?t=1387455](http://ubuntuforums.org/showthread.php?t=1387455)

While this is a known and confirmed bug it only seems to affect some people.
As far as resolving - better to take it on yourself to find a way, if any, than wait for a fix that may never come (at least w/ the current version you're using

---

### Post by Petrolea on 2011-05-23
There's a thread already running about this huge memory leak, it is a problem for many people around here. I have this issue too, while running through the video RAM gets exhausted and everything starts to freeze.

---

### Post by mc4man on 2011-05-23
> **tmcmurph said:**
> I've tried alsa and same thing.
While the issue is just not with pulse - just setting vlc to use alsa doesn't mean it still isn't using pulse - confirm while vlc is playing by looking  in sound pref.'s > Applications' tab, should be empty

---

