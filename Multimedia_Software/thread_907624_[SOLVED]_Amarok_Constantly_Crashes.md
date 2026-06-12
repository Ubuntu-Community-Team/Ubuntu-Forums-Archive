---
title: "[SOLVED] Amarok Constantly Crashes"
date: 2008-09-01
forum: Multimedia Software
---

### Post by Artery on 2008-09-01
Amarok constantly crashes for me, sometimes it works, most times it doesnt.  When i try to play a song, I can see the levels bars at the bottom start moving, and then freeze after about a second and no audio.  I followed the comprehensive guide at the top of this category and reinstalled alsa.  Previous to doing this, when amarok crashed, i couldnt play files with the default music player, but now the default player works even when amarok crashes. I have already tried uninstalling and reinstalling amarok.  

If the answer is just that amarok is a buggy player, let me know of a better one, I just want something that is good at organizing a large amount of music.  

Hope this is the right category to post this question.

---

### Post by minky311 on 2008-09-01
Try starting amarok in the terminal by going to Applications->Accessories->Terminal and typing in amarokapp.
Then posting the output here to see if it spews out any errors.

---

### Post by Artery on 2008-09-01
I did that and this is what comes out...I have *no* idea what it means

```
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ccd0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ccd0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image

```

For now I'm using banshee, which seems to work pretty well

---

### Post by minky311 on 2008-09-01
Did amarok crash during that ouput if not could you get the ouput and post it here when it crashes?

---

### Post by Artery on 2008-09-01
It didn't crash that time, but it did later, when I checked the text in the terminal, nothing new was there.

---

### Post by minky311 on 2008-09-01
Could you go into synaptic package manager by going to System->Administration->Synaptic package manager and searching for libxine.
Then making sure you have libxine1-gnome and libxine1-ffmpeg installed.
Have you checked to make sure that amarok is using the right audio settings by going to Settings->Configure Amarok->Engine.

---

### Post by Despot Despondency on 2008-09-03
Hey, sorry to butt in on your post but I seem to be having exactly the same problem. When I ran amarokapp in the terminal I got 

> 
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d750 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d750 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP


Then when I got an error nothing new occurred in the terminal. Amarok is pointing to the xine engine. I assume this is correct? I didn't have libxine1-gnome installed, so I installed it and it doesn't seem to have made a difference. Any other suggestions?

---

### Post by Artery on 2008-09-04
> **minky311 said:**
> Could you go into synaptic package manager by going to System->Administration->Synaptic package manager and searching for libxine.
Then making sure you have libxine1-gnome and libxine1-ffmpeg installed.
Have you checked to make sure that amarok is using the right audio settings by going to Settings->Configure Amarok->Engine.

Both of those werent installed, they are now, so far so good, amarok hasnt crashed.  Thanks!

---

### Post by kiisu on 2008-09-04
I just started getting these issues with Amarok.
Before upgrading to Hardy earlier this week I never had a problem.
I'm giving the suggestions here a try and will report back.

---

### Post by Despot Despondency on 2008-09-06
I retract my previous statement, it has made some difference. Amarok is definitely crashing less than it was before. However, I've noticed that it tends to crash when I've been using flash, on youtube for example.

---

### Post by Uniq PhoeniX on 2008-09-16
Same problem, fixed by restarting FireFox session. I also seem to get it in FireFox with videos playing only for 2-4 sec and browser restart fixes it. Has also happened on Win XP

---

