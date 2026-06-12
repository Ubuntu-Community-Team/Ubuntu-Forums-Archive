---
title: "Is VLC video player just trash, or am I doing something wrong?"
date: 2021-01-20
forum: Multimedia Software
---

### Post by Swan_DB on 2021-01-20
Audio doesn't work, it puts a little red circle in the top/right header and every time I open the VLC is adds a new icon in that same spot, the top/right header..

DELETE this post.

---

### Post by ajgreeny on 2021-01-20
Did you solve this problem?
If so please tell us what that solution was.

---

### Post by slickymaster on 2021-01-20
*Thread moved to **Multimedia Software**.*

---

### Post by Swan_DB on 2021-01-21
The VLC icon shows up for every new video I open in the header (near the settings/power/shutdown bar).  Is this due to snap install?  Should I try .deb install?  Is there a better mp4 video player?

Am I not exiting the VLC program properly?  Leaving it running in the background?

[B][SOLVED]  If you hit the X in the upper right corner to close the window (like you would in Windows 7), it leaves the process running; if you go to Media -> Quit (Ctrl + Q), it ends the process, seemingly, correctly.  

Is this a bug?[/B]

I have solved this issue in another thread, should I delete this thread and maybe one more "useless" thread, and just leave the one with the actual solution?  Or just copy/paste solution into all two/three threads and mark them all as SOLVED?

Here is the [SOLVED] correctly thread: [https://ubuntuforums.org/showthread.php?t=2456926](https://ubuntuforums.org/showthread.php?t=2456926)

[https://ubuntuforums.org/showthread.php?t=2456926](https://ubuntuforums.org/showthread.php?t=2456926)

---

### Post by QIII on 2021-01-21
Threads merged.

---

### Post by Swan_DB on 2021-01-21
Not sure where to post this, but I think the VLC Player (Media/Video Player) and the Snap Store don't work well together.  I killed the Snap process, and VLC Player seems to work well now...  i'm gonna try to find a .deb package for VLC Player.

[SOLVED] sort of

edit 2: maybe snap package does something with the VLC Player's cache?  Just a hunch.

---

### Post by CelticWarrior on 2021-01-22
No, it isn't related with snap or not snap.
The same problem of the hanging process has been noticed recently with both versions.

---

### Post by SeijiSensei on 2021-01-22
smplayer + mpv for the win

---

### Post by ajgreeny on 2021-01-22
I am mystified still by this thread.

Did you have the snap version of VLC installed or the .deb repository version?
What version of VLC was that and which version of Ubuntu are you using?

I do not normally use VLC for audio, preferring the lower resource use of audacious, and reserving VLC for videos.  However if I use VLC for audio files (of any type) it plays without problem and always fully closes when I use the X at top right of the window.

I do not use snaps at all and have removed snap-store from my system but I have no idea if snap-store has anything to do with your problem.

---

### Post by CelticWarrior on 2021-01-23
VLC always worked for me before and always behaved as expected when closing, no matter the way it was closed. But recently I've noticed that sometimes - it has nothing to do with the way it was closed, unlike what the OP reported -, randomly, its process seems to be stuck and an icon persists. Usually it opens another one and another one after that, keeping a sort of christmas tree lights in the tray with multiple orange cones. What I usually do is to kill the misbehaving processes.

Why this is happening I don't know. Here are the facts:
It happens regardless of the version, snap or deb.
It happens regardless of the way it is closed.
It's random, it can be OK for days and then get back to misbehaving on close.

---

### Post by ajgreeny on 2021-01-23
I have VLC settings to open one instance only; I wonder if this setting might make any difference to this problem?

---

### Post by scottbomb on 2021-01-23
VLC has been acting up on my living room PC lately, so bad I've uninstalled it and started using Dragon Player (though I'm on the hunt for a video player where I can permanently disable subtitles). Anyhow, if it runs at all, after about a minute it seems to get stuck on a frame while the audio continues and the video consist of 2 or 3 frames rapidly repeating. It works fine on the other PCs in the house so who knows? The living room PC does drive 3 monitors so maybe that has something to do with it. I still blame VLC over the video card or anything else because Dragon Player plays the same videos just fine.

---

### Post by CelticWarrior on 2021-01-24
> **ajgreeny said:**
> I have VLC settings to open one instance only; I wonder if this setting might make any difference to this problem?
Apparently it does make a difference but then it hasn't been happening in the last few days even without that setting.

---

