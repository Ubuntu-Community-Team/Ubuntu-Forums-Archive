---
title: "Mplayer problems"
date: 2008-04-30
forum: Multimedia Software
---

### Post by jaemate21 on 2008-04-30
Hey Ubuntu folks!I have been using ubuntu for while now,the feisty fawn one and I have recently installed Mplayer,the songs work realy well,but the issue is playing movies.I use the nvidia card,I have installed the drivers and I know it works well(I can do the desktop effect stuff with no complains).It(Mplayer) started out saying "error initializing the selected driver".I read on the forums about the vidix drivers so I went and got the software but it still doesnt play movies(ie I still get the same error as before).I am really frustrated to the limit.If anyone can give me some solution it will be greatly appreciated.I like ubuntu and I dont wanna go elsewhere.

---

### Post by cor2y on 2008-04-30
It sounds like its the video output mplayer is using is set incorrectly
Change your video output selection in mplayer.
Right click anywhere on mplayer select Preferences and go to the video tab.
Select x11 or one of the other selections than what you have.
Close the preferences window , then replay the movie from the beginning and see what happens.

---

