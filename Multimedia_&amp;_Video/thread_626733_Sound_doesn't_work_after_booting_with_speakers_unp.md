---
title: "Sound doesn't work after booting with speakers unplugged"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by shockwaver on 2007-11-29
Ok, I'm having a really annoying problem. Last night I unplugged my speakers to take them with me somewhere. Came back, noticed that my volume icon had an X on it. Didn't think to much of it, shut my computer down, and rebooted it in the morning. Same X, so I plug my speakers back in, but nothing. No sound, nothing. So I think, "Ok, maybe I need to reboot with the speakers plugged in.", so I do. The sound plays at the gdm log in (the quick bongo drum thing), log in.. no sound. Same damn X. Double click the icon, and I get
```
No volume control GStreamer plugins and/or devices found.
```
But, I -know- it works. It plays the sound when gdm starts up. Any advice would be most helpful.

Oh, running 7.10 BTW.

---------------
EDIT
Solved. In my newbness, I had forgotten that a day or so ago I had accidently removed my user from all the groups it was in, and I didn't realize audio was a seperate group.

---

