---
title: "Mplayer won't work"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by es-brusv on 2006-12-15
When i try to open any of my movies I only get this error:

Error opening/initializing the selected video_out (-vo) device

Any body know how to fix this?

I am running Ubuntu Edgy....

---

### Post by kapilg_it on 2006-12-15
right click mplayer go to preferences , in video suboption choose X11(openGL) multiple texture version.

applies if you are using GUI mplayer. 
check if it does solve the problem :-k

---

### Post by Face2thehighfog on 2006-12-15
I was having the same problem with mplayer and followed your directions.  Seems to work like a charm! THANKS!  Although everything seems to play ok, I still get error messages like "Could Not Open Codec" (it does play, however) and "Requested audio codec family [mp3] (afm=mp3lib) not available.  Enable it at compilation."
Although no of these seem to affect (effect? -- you would think I never graduated HS) the video and audio playback, I wonder if this will come back to bite me later on.  

Also, I read earlier that I could just edit the .conf file to change the VO (as opposed to going to "Preferences" etc.) but could not find the .conf file.  Is there a central repository for this (I just figured out what gconfig-edit is but I still couldn't find it).

Thank you so much.

V/r

Ryan

PS if I am not in the right thread, I apologize, a point in the right direction would set me straight.  Thanks.  *newbie apologizes*

---

### Post by kapilg_it on 2006-12-17
to remove this error go to codecs tab -> audio -> choose ffmpeg 
such problems are asked every time :D

---

### Post by es-brusv on 2006-12-18
Thanks all this helped. Now it plays without any problems.

Thank you all :D

---

