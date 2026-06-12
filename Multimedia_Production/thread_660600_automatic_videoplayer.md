---
title: "automatic videoplayer"
date: 2008-01-06
forum: Multimedia Production
---

### Post by ringirugladi on 2008-01-06
Hello, I need to have a videofile played up automaticly when booted. So the account will be accessed automaticly and a video file will start playing automaticly fullscreen. Is there a console player which can do this or can I use VLC for example?

RingiR

---

### Post by disturbed1 on 2008-01-07
VLC can be started in full screen mode

Open VLC,  get to the preferences put a check in Fullscreen video output. Goto to the system menu, choose Preferences, then sessions. Under the Startup Programs tab, add a program.

Something like
vlc /path/here/file.avi

or 

mplayer -fs /path/here/file.avi

---

