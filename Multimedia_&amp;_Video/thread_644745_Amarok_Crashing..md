---
title: "Amarok Crashing."
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by karachuonyo on 2007-12-19
I love amarok and think it's the best player in linux. However the last week or so when i click on the amarok icon to play my music nothing happens and i have to drop to konsole to kill the process. If i then start amarok it will play flawlessly with no issues whatever. I have attached the messages from konsole when i try starting amarok from the terminal.
:~$ amarokapp
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81e1cc0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81e1cc0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP
Killed

---

### Post by Capricori on 2007-12-19
I get this when using Amarok over SSH, and it's never caused me any problems. There's a chance that it is unrelated to your issue.
I agree about it being the best player though, I hope you fix your problem :)

Regards, 

Capricori

---

