---
title: "[SOLVED] Watch TV and Recording Playback Issues"
date: 2008-06-15
forum: Mythbuntu
---

### Post by chrisblue on 2008-06-15
[FONT=monospace]Hi. Trying to install Mythbuntu for the first time and having issues getting any playback.

I have two leadtek DVT100T tuners installed. They both appear to have installed correctly and can scan successfully for the local channels and can schedule recordings from the program guide, which appear to record.

However when I try to play back these recordings through Myth they are severely ghosted (vertically) and colour split to predominantly green (like looking at a 3d movie without the glasses).

Edit: I should also add that the preview window on the recordings library shows the clip perfectly and when watching it green and ghosted (as above) if I fast forward it seems to be pretty normal. Still can't watch Live TV though.

If I try to watch live TV after a moment of blank screen the front end menu comes up again.

However when I look in the recordings folder I can play back the recordings made perfectly using the Totem Movie Player.

Any ideas on what I can do to fix this?

Thanks. 

Mythbuntu: 0.21.0+fixes16838-0ubuntu3 on Ubuntu Hardy Heron 8.04

Edit
============================
Turned out to be a permissions issue for the recording folder. Fixed that and all seems to be working ok.



[/FONT]

---

### Post by chrisblue on 2008-06-15
OK Solved one issue - playback of recorded media. Changed the Current Video Playback Profile to CPU-- and it looks fine.

---

### Post by chrisblue on 2008-06-18
Still can't watch TV directly. Possibly there isn't a default channel chosen in the back end - can anyone point me towards how or where I can set one?

Thanks

---

### Post by jlagrone on 2008-06-18
The default channel is chosen in mythbackend setup, I believe it is in inputs directly below where you chose the source for a particular input.  If you can scan and record, you probably already have one set; however, I've noticed some of the channels the scan picks up for me come and go (or aren't really a channel) and sometimes when I don't get a lock (or it gets some kind of pseudo-lock) it will crash like you describe.  If I remove these channels (so I can't accidentally change to them) and change the starting channel in mythbackend to a channel I know works (ie one you have recorded from) everything works fine.

---

### Post by chrisblue on 2008-06-20
Thanks for that. I did find where to set the starting channel unfortunatly that didn't help. I rescanned channels on both cards and still can only record the TV signal and can't view it via the WatchTV button.

One other thing I have noticed is that when myth is recording a program it breaks it up into quite a few different files some of which appear to have no recording associated with them. Is that supposed to happen or am i missing something else.

I installed Mythbuntu over an existing Hardy install, should I just bite the bullet and put Mythbuntu on its own partition and re install?

---

