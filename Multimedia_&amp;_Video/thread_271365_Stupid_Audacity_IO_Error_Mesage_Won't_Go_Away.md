---
title: "Stupid Audacity I/O Error Mesage Won't Go Away"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by Mark76 on 2006-10-04
Even when I use the killall esd command

Is it a different command in Dapper?

---

### Post by dolson on 2006-10-05
Do you have anything else open that is using the audio device? Close everything, even web browsers, Gaim, etc.

And you didn't even say what the error message is so it could be telling you anything...

---

### Post by Mark76 on 2006-10-05
I unchecked "Play system sounds" in System-Preferences-Sounds, rebooted and it went away.

So it looks like that might have been the answer.

---

### Post by dolson on 2006-10-05
That is using esd though, so the killall -9 esd should have worked for you the first time. Well, at least it's working now.

---

